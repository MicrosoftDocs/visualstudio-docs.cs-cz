---
title: Izolace testů jednotek pro aplikace SharePoint 2010 pomocí emulátorů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: b681164c-c87a-4bd7-be48-ed77e1578471
caps.latest.revision: 17
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cc3560c1cbcebea9f61465240cd4e2c7a0f811f7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667470"
---
# <a name="using-emulators-to-isolate-unit-tests-for-sharepoint-2010-applications"></a>Izolace testování částí aplikací pro SharePoint 2010 s použitím emulátorů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Balíček Microsoft. SharePoint. emulátory poskytuje sadu knihoven, které vám pomůžou vytvořit izolované testy jednotek pro aplikace Microsoft SharePoint 2010. Emulátory používají [překrytí](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) z rozhraní pro izolaci [falešného kódu společnosti Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md) k vytváření lehkých objektů v paměti, které napodobují nejběžnější objekty a metody rozhraní API služby SharePoint. Pokud není metoda služby SharePoint emulovana nebo pokud chcete změnit výchozí chování emulátoru, můžete vytvořit napodobeniny Shim k poskytnutí výsledků, které chcete.

 Existující testovací metody a třídy lze snadno převést na běh v kontextu emulátoru. Tato funkce umožňuje vytvořit testy dvojího použití. Test dvojího použití může přepínat mezi testy integrace s reálným rozhraním API služby SharePoint a izolovanými testy jednotek, které používají emulátory.

## <a name="BKMK_In_this_topic"></a>V tomto tématu
 [Požadavky](#BKMK_Requirements)

 [Příklad AppointmentsWebPart](#BKMK_The_AppointmentsWebPart_example)

 [Převod existujícího testu](#BKMK_Converting_an_existing_test)

- [Přidání balíčku emulátory do testovacího projektu](#BKMK_Adding_the_Emulators_package_to_a_test_project)

- [Spuštění testovací metody s emulací](#BKMK__Running_a_test_method_in_the_emulation_context)

  [Vytváření tříd a metod dvojího použití](#BKMK_Creating_dual_use_classes_and_methods)

  [Použití atributů TestInitialize a TestCleanup k vytvoření testovací třídy se dvěma možnostmi použití](#BKMK_Using_TestInitialize_and_TestCleanup_attributes_to_create_a_dual_use_test_class)

  [Zpracování neemulovaných metod služby SharePoint](#BKMK_Handling_non_emulated_SharePoint_methods)

  [Zápis testů emulace od začátku a souhrnu](#BKMK_Writing_emulation_tests_from_scratch__and_a_summary)

  [Příklad](#BKMK_Example)

  [Emulované typy služby SharePoint](#BKMK_Emulated_SharePoint_types)

## <a name="BKMK_Requirements"></a>Požadavků

- Microsoft SharePoint 2010 (SharePoint 2010 Server nebo SharePoint 2010 Foundation)

- Microsoft Visual Studio Enterprise

- Balíček NuGet emulátorů služby Microsoft SharePoint

  Měli byste se také seznámit se [základy testování částí v aplikaci Visual Studio](../test/unit-test-basics.md) a některými znalostmi [napodobenin společnosti Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="BKMK_The_AppointmentsWebPart_example"></a>Příklad AppointmentsWebPart
 AppointmentsWebPart umožňuje zobrazit a spravovat SharePointový seznam vašich schůzek.

 ![Webová část události](../test/media/ut-emulators-appointmentswebpart.png "UT_EMULATORS_AppointmentsWebPart")

 V tomto příkladu budeme testovat dvě metody webové části:

- Metoda `ScheduleAppointment` ověří hodnoty položky seznamu předané metodě a vytvoří novou položku v seznamu na zadaném webu služby SharePoint.

- Metoda `GetAppointmentsForToday` vrací podrobnosti o dnešních událostech.

  [V tomto tématu](#BKMK_In_this_topic)

## <a name="BKMK_Converting_an_existing_test"></a>Převod existujícího testu
 V typickém testu metody v součásti služby SharePoint vytvoří testovací metoda dočasný web ve službě SharePoint Foundation a přidá komponenty služby SharePoint do webu, který testovaný kód vyžaduje. Testovací metoda potom vytvoří a vykonává instanci komponenty. Na konci testu dojde k přerušení webového serveru.

 Metoda `ScheduleAppointment` testovaného kódu je pravděpodobně jednou z prvních metod napsaných pro komponentu:

```
// method under test
public bool ScheduleAppointment(SPWeb web, string listName, string name,
    string phone, string email, string age, DateTime date, out string errorMsg)
{
    errorMsg = string.Empty;
    var badFormat = this.checkInput(name, phone, email, age);
    if (badFormat)
    {
        errorMsg = "Bad Format";
        return false;
    }
    var exists = this.CheckDuplicate(listName, web, name, phone, email, age, date);
    if (exists)
    {
        errorMsg = "Item already exists";
        return false;
    }
    SPListItemCollection items = web.Lists[listName].Items;
    // create item and populate fields
    SPListItem item = items.Add();
    item["Name"] = name;
    item["Phone"] = phone;
    item["Email"] = email;
    item["Age"] = age;
    item["Date"] = date.ToString("D");
    item.Update();
    return true;
}

```

 První test funkce v `ScheduleAppointment` metoda může vypadat takto:

```csharp

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}
```

 I když tato testovací metoda ověřuje, že metoda `ScheduleAppointment` správně přidá novou položku do seznamu, je více integrační test webové části, než test konkrétního chování kódu. Externí závislosti na SharePoint a rozhraní API služby SharePoint můžou způsobit selhání testu z jiných důvodů než uživatelského kódu v metodě `ScheduleAppointment`. Režie při vytváření a zničení webu služby SharePoint může také způsobit, že test je příliš pomalý pro spuštění jako běžná součást procesu kódování. Při provádění nastavení a zničení lokality pro každou zkušební metodu je pouze problém vytváření efektivních testů jednotek pro vývojáře.

 Emulátory služby Microsoft SharePoint poskytují sadu objektů a metod "Double", které napodobují chování nejběžnějších rozhraní API služby SharePoint. Emulované metody jsou jednoduché implementace rozhraní API služby SharePoint, které nevyžadují spuštění služby SharePoint. Pomocí společnosti Microsoft napodobeniny k prohlídce volání rozhraní API služby SharePoint do metody, které jsou na obou emulátorech služby SharePoint, izolujete testy a ujistěte se, že testujete požadovaný kód. Při volání metod služby SharePoint, které nejsou emulované, můžete použít napodobeniny přímo k vytvoření požadovaného chování.

 [V tomto tématu](#BKMK_In_this_topic)

### <a name="BKMK_Adding_the_Emulators_package_to_a_test_project"></a>Přidání balíčku emulátory do testovacího projektu
 Chcete-li přidat emulátory služby SharePoint do testovacího projektu:

1. Vyberte projekt testů v Průzkumník řešení.

2. V místní nabídce vyberte **Spravovat balíčky NuGet...**

3. Vyhledejte v **online** kategorii `Microsoft.SharePoint.Emulators` a zvolte možnost **nainstalovat**.

   ![Balíček NuGet emulátorů SharePointu](../test/media/ut-emulators-nuget.png "UT_EMULATORS_Nuget")

   [V tomto tématu](#BKMK_In_this_topic)

### <a name="BKMK__Running_a_test_method_in_the_emulation_context"></a>Spuštění testovací metody s emulací
 Instalace balíčku přidá do vašich projektů odkazy na požadované knihovny. Aby bylo možné snadno používat emulátory v existující testovací třídě, přidejte obory názvů `Microsoft.SharePoint.Emulators` a `Microsoft.QualityTools.Testing.Emulators`.

 Chcete-li povolit emulaci v testovacích metodách, zabalte tělo metody v příkazu `using`, který vytvoří objekt `SharePointEmulationScope`. Příklad:

```csharp

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    // create the emulation scope with a using statement
    using (new SharePointEmulationScope())
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}

```

 Při spuštění testovací metody volá modul runtime emulátoru společnosti Microsoft napodobeniny k dynamickému vkládání kódu do metod služby SharePoint, aby bylo možné přesměrovat volání těchto metod na delegáty deklarované v souboru Microsoft. SharePoint. napodobeniny. dll. Microsoft. SharePoint. Emulátors. dll implementuje delegáty pro emulované metody, a to pečlivě mimicking skutečné chování služby SharePoint. V případě, že metoda testu nebo zkoušená součást volá metodu služby SharePoint, chování, které je výsledkem emulace.

 ![Tok provádění emulátoru](../test/media/ut-emulators-flowchart.png "UT_EMULATORS_FlowChart")

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="BKMK_Creating_dual_use_classes_and_methods"></a>Vytváření tříd a metod dvojího použití
 Chcete-li vytvořit metody, které lze použít pro integrační testy proti skutečnému rozhraní API služby SharePoint a izolované testy jednotek, které používají emulátory, použijte přetížený konstruktor `SharePointEmulationScope(EmulationMode)` k zabalení kódu testovací metody. Dvě hodnoty výčtu `EmulationMode` určují, zda obor používá emulátory (`EmulationMode.Enabled`) nebo zda obor používá rozhraní API služby SharePoint (`EmulationMode.Passthrough`).

 Tady je příklad, jak můžete změnit předchozí test na duální použití:

```csharp

// class level field specifies emulation mode
private const EmulationMode emulatorMode = EmulationMode.Enabled;

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    // emulation scope determined by emulatorMode
    using( SharePointEmulationScope(emulatorMode))
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}
```

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="BKMK_Using_TestInitialize_and_TestCleanup_attributes_to_create_a_dual_use_test_class"></a>Použití atributů TestInitialize a TestCleanup k vytvoření testovací třídy se dvěma možnostmi použití
 Pokud spustíte všechny nebo většinu testů ve třídě pomocí `SharePointEmulationScope`, můžete využít techniky na úrovni třídy pro nastavení režimu emulace.

- Metody testovací třídy, které se s <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> můžou vytvořit a zničit obor.

- Nastavení `EmulationMode` na úrovni třídy vám umožní automatizovat změnu režimu mezi `EmulationMode.Enabled` a `EmulationMode.Passthrough`.

  Metoda třídy s atributem `[TestInitialize]` je spuštěna na začátku každé testovací metody a metoda, která je označena `[TestCleanup]` spouštěna na konci každé testovací metody. Můžete deklarovat soukromé pole pro objekt `SharePointEmulationScope` na úrovni třídy, inicializovat jej v metodě `TestInitialize` s atributy a následně vyřadit objekt v metodě `TestCleanup` s atributy.

  Můžete použít libovolnou metodu, kterou zvolíte pro automatizaci výběru `EmulationMode`. Jedním ze způsobů, jak kontrolovat existenci symbolu pomocí direktiv preprocesoru. Chcete-li například spustit testovací metody ve třídě pomocí emulátorů, můžete definovat symbol, jako je například `USE_EMULATION` v souboru testovacího projektu nebo na příkazovém řádku sestavení. Pokud je symbol definován, je deklarace třídy `EmulationMode` konstanta deklarována a nastavena na hodnotu `Enabled`. V opačném případě je konstanta nastavena na `Passthrough`.

  Zde je příklad třídy testu, která ukazuje, jak použít direktivy preprocesoru a metody `TestInitialize` a `TestCleanup` atributů pro nastavení režimu emulace.

```csharp
//namespace declarations
...

namspace MySPAppTests
{
    [TestClass]
    public class BookAnAppointmentWebPartTests
    {

        // emulationScope is a class level field
        private SharePointEmulationScope emulationScope;

        // preprocessor directives determine the value of emulatorMode
        #if USE_EMULATIONprivate const EmulationMode emulatorMode = EmulationMode.Enabled;#elseprivate const EmulationMode emulatorMode = EmulationMode.Passthrough;#endif

        // InitializeTest sets the emulation scope at the beginning of each test method
        [TestInitialize]public void InitializeTest(){this.emulationScope = new SharePointEmulationScope(emulatorMode);}

        // CleanupTest disposes the emulation scope at the end of each test method
        [TestCleanup]public void CleanupTest(){this.emulationScope.Dispose();}

        [TestMethod]
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
        {
            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                string errorMsg = string.Empty;
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);

                // Act
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
                    out errorMsg);
                list.Delete()

                // Assert
                Assert.IsTrue(success);
            }
        }

        ...// More tests

    }
}

```

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="BKMK_Handling_non_emulated_SharePoint_methods"></a>Zpracování neemulovaných metod služby SharePoint
 Ne všechny typy služby SharePoint jsou emulované a ne všechny metody v některých emulovaných typech jsou emulované. Pokud testovaný kód volá metodu služby SharePoint, která není emulovana, metoda vyvolá výjimku `NotSupportedException`. Pokud dojde k výjimce, přidáte do metody služby SharePoint Shim pro vložení falešného kódu.

 **Nastavení napodobenin na SharePointu**

 Pro explicitní volání překrytí napodobenin společnosti Microsoft:

1. Chcete-li překrýt třídu služby SharePoint, která není emulovana, upravte soubor Microsoft. SharePoint. napodobeniny a přidejte třídu do seznamu tříd překryté. Přečtěte si část [Konfigurace generování kódu zástupných procedur a překrytí](https://msdn.microsoft.com/library/hh708916.aspx#bkmk_configuring_code_generation_of_stubs) [v části generování kódu, kompilace a konvence pojmenování v tématu Microsoft napodobeniny](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md).

    ![Napodobenina složka v Průzkumník řešení](../test/media/ut-emulators-fakesfilefolder.png "UT_EMULATORS_FakesFileFolder")

2. Znovu sestavte projekt testů alespoň jednou po instalaci balíčku emulátory služby Microsoft SharePoint a pokud jste upravili soubor Microsoft. SharePoint. napodobenin. Sestavení projektu vytvoří a naplní složku **FakesAssembly** v kořenové složce projektu na disku.

    ![FakesAssembly složka](../test/media/ut-emulators-fakesassemblyfolder.png "UT_EMULATORS_FakesAssemblyFolder")

3. Přidejte odkaz na sestavení **Microsoft. SharePoint. 14.0.0.0. napodobenins. dll** , které je umístěno ve složce **FakesAssembly** .

4. Volitelné Přidejte direktivu Namespace pro do třídy testu pro `Microsoft.QualityTools.Testing.Fakes`, `Microsoft.SharePoint.Fakes` a libovolného vnořeného oboru názvů `Microsoft.SharePoint.Fakes`that, který chcete použít.

   **Implementace delegáta překrytí pro metodu služby SharePoint**

   V našem ukázkovém projektu metoda `GetAppointmentsForToday` volá metodu rozhraní API služby SharePoint [SPList. GetItems (SPQuery)](https://msdn.microsoft.com/library/ms457534.aspx) .

```csharp
// method under test
public string GetAppointmentsForToday(string listName, SPWeb web)
{
    SPList list = web.Lists[listName];
    DateTime today = DateTime.Now;
    var listQuery = new SPQuery{Query = String.Format("<Where><Eq><FieldRef Name='Date'/>" +"<Value Type='Text'>{0}</Value>" +"</Eq></Where>", today.ToString("D"))};
    var result = new System.Text.StringBuilder();
    foreach (SPListItem item in list.GetItems(listQuery))
    {
        result.AppendFormat("Name: {0}, Phone: {1}, Email: {2}, Age: {3}, Date: {4}\n",
            item["Name"], item["Phone"], item["Email"], item["Age"], item["Date"]);
    }
    return result.ToString();
}

```

 Verze `SPList.GetItems(SPQuery)` přetížené `GetItems` metody není emulovaná. Proto pouze zabalení stávajícího testu pro `GetAppointmentsForToday` v `SharePoint.Emulation.Scope` selže. Chcete-li vytvořit pracovní test, je nutné napsat implementaci falešného delegáta `ShimSPList.GetItemsSPQuery`, který vrátí výsledky, proti kterým chcete testovat.

 Zde je úprava stávající testovací metody, `GetAppointmentsForTodayReturnsOnlyTodaysAppointments`, která implementuje delegáta napodobeniny. Požadované změny jsou vyvolány v komentářích:

> [!IMPORTANT]
> Testovací metody, které explicitně vytvářejí napodobeniny, vyvolávají výjimku `ShimNotSupported` při spuštění testu v kontextu `EmulationMode.Passthrough`. Chcete-li se tomuto problému vyhnout, použijte proměnnou pro nastavení hodnoty `EmulationMode` a zabalte jakýkoliv falešný kód v příkazu `if`, který testuje hodnotu.

```csharp
// class level field to set emulation mode
private const EmulationMode emulatorMode = EmulationMode.Enabled

[TestMethod]
public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()
{

    // create the emulation scope with a using statement
    using (var emulationScope = new SharePointEmulationScope(emulatorMode))
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);
        // insert 2 items into list
        AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",
            "raisa@outlook.com", "55", date.ToString("D") });
        AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",
            "francis@contoso.com", "42", date.AddDays(1).ToString("D") });

        // use Fakes shims only if emulation is enabled
        if (emulatorMode == EmulationMode.Enabled){var sList = new ShimSPList(list);sList.GetItemsSPQuery = (query) =>{var shim = new ShimSPListItemCollection();shim.Bind(new[] { list.Items[0] });return shim.Instance;}}

        // Act
        string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);
        list.Delete();

        // Assert
        Assert.IsTrue(result.Contains(String.Format(
            "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +
            "Age: 55, Date: {0}", date.ToString("D"))));
        Assert.IsFalse(result.Contains("Name: Francis Totten"));
    }
}

```

 V této metodě nejdřív otestujeme, že emulace je povolená. Pokud je to, vytvoříme pro náš `SPList`ový seznam napodobeninu a potom pro jeho `GetItemsSPQuery` delegáta vytvoříte a přiřadíme metodu. Delegát používá metodu `Bind` napodobeniny k přidání správné položky seznamu do `ShimSPListItemCollection`, který je vrácen volajícímu.

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="BKMK_Writing_emulation_tests_from_scratch__and_a_summary"></a>Zápis testů emulace od začátku a souhrnu
 I když postupy pro vytvoření emulace a testů dvojího použití, které jsou popsány v předchozích částech, předpokládají, že převádíte stávající testy, můžete také použít techniky k psaní testů od začátku. Následující seznam shrnuje tyto techniky:

- Chcete-li použít emulátory v testovacím projektu, přidejte do projektu balíček NuGet Microsoft. SharePoint. emulátory.

- Chcete-li použít emulátory v testovací metodě, vytvořte objekt `SharePointEmulationScope` na začátku metody. Všechna podporovaná rozhraní API služby SharePoint budou emulovana, dokud nebude rozsah vyřazen.

- Napište svůj testovací kód, jako kdybyste ho napsali do reálného rozhraní API služby SharePoint. Kontext emulace automaticky rozjezde volání metod služby SharePoint na jejich emulátory.

- Ne všechny objekty služby SharePoint jsou emulované, a ne všechny metody pro některé emulované objekty jsou emulované. Výjimka `NotSupportedException` je vyvolána při použití neemulovaného objektu nebo metody. Pokud k tomu dojde, explicitně vytvořte delegáta překrytí falešného kódu pro metodu, která vrátí požadované chování.

- Chcete-li vytvořit testy dvojího použití, použijte konstruktor `SharePointEmulationScope(EmulationMode)` k vytvoření objektu oboru emulace. Hodnota `EmulationMode` určuje, zda jsou volání služby SharePoint emulovana nebo provedena na skutečném webu služby SharePoint.

- Pokud se všechny nebo většina testovacích metod v testovací třídě spustí v kontextu emulace, můžete použít metodu `TestInitialize` atributů na úrovni třídy pro vytvoření objektu `SharePointEmulationScope` a pole na úrovni třídy pro nastavení režimu emulace. To vám pomůže automatizovat změnu režimu emulace. Pak použijte `TestCleanup` metodu s atributem k Dispose objektu Scope.

  [V tomto tématu](#BKMK_In_this_topic)

## <a name="BKMK_Example"></a>Případě
 Zde je konečný příklad, který zahrnuje techniky emulátoru služby SharePoint, které jsou popsány výše:

```csharp
using System;
//other namespace declarations
...
// code under test
using MySPApps;
using Microsoft.SharePoint;
// unit testing and emulators
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.QualityTools.Testing.Emulators;
using Microsoft.SharePoint.Emulators;
// explicit Fakes shims
using Microsoft.QualityTools.Testing.Fakes;
using Microsoft.SharePoint.Fakes

namspace MySPAppTests
{
    [TestClass]
    public class BookAnAppointmentWebPartTests
    {

        // emulationScope is a class level field
        private SharePointEmulationScope emulationScope;

        // preprocessor directives determine the value of emulatorMode
        #if USE_EMULATION
            private const EmulationMode emulatorMode = EmulationMode.Enabled;
        #else
            private const EmulationMode emulatorMode = EmulationMode.Passthrough;
        #endif

        // InitializeTest sets the emulation scope at the beginning of each test method
        [TestInitialize]
        public void InitializeTest()
        {
            this.emulationScope = new SharePointEmulationScope(emulatorMode);
        }

        // CleanupTest disposes the emulation scope at the end of each test method
        [TestCleanup]
        public void Cleanup()
        {
            this.emulationScope.Dispose();
        }

        [TestMethod]
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
        {
            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                string errorMsg = string.Empty;
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);

                // Act
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
                    out errorMsg);
                list.Delete()

                // Assert
                Assert.IsTrue(success);
            }
        }

        [TestMethod]
        public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()
        {

            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);
                // insert 2 items into list
                AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",
                    "raisa@outlook.com", "55", date.ToString("D") });
                AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",
                    "francis@contoso.com", "42", date.AddDays(1).ToString("D") });

                // use Fakes shims only if emulation is enabled
                if (emulatorMode == EmulationMode.Enabled)
                {
                    var sList = new ShimSPList(list);

                    sList.GetItemsSPQuery = (query) =>
                    {
                        var shim = new ShimSPListItemCollection();
                        shim.Bind(new[] { list.Items[0] });
                        return shim.Instance;
                    }
                }

                // Act
                string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);
                list.Delete();

                // Assert
                Assert.IsTrue(result.Contains(String.Format(
                    "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +
                    "Age: 55, Date: {0}", date.ToString("D"))));
                Assert.IsFalse(result.Contains("Name: Francis Totten"));
            }
        }

        ...// More tests

    }
}

```

## <a name="BKMK_Emulated_SharePoint_types"></a>Emulované typy služby SharePoint
 [Microsoft. SharePoint. SPField](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPField)

 [Microsoft. SharePoint. SPFieldIndex](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndex)

 [Microsoft. SharePoint. SPFieldIndexCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndexCollection)

 [Microsoft. SharePoint. SPFieldLink](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLink)

 [Microsoft. SharePoint. SPFieldLinkCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLinkCollection)

 [Microsoft. SharePoint. SPFieldUrlValue](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldUrlValue)

 [Microsoft. SharePoint. SPFile](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFile)

 [Microsoft. SharePoint. SPFileCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFileCollection)

 [Microsoft. SharePoint. SPFolder](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolder)

 [Microsoft. SharePoint. SPFolderCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolderCollection)

 [Microsoft. SharePoint. SPItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPItem)

 [Microsoft. SharePoint. SPItemEventDataCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventDataCollection)

 [Microsoft. SharePoint. SPItemEventProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventProperties)

 [Microsoft. SharePoint. SPList](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPList)

 [Microsoft. SharePoint. SPListCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPListCollection)

 [Microsoft. SharePoint. SPListEventProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPListEventProperties)

 [Microsoft. SharePoint. SPListItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItem)

 [Microsoft. SharePoint. SPListItemCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItemCollection)

 [Microsoft. SharePoint. SPQuery](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPQuery)

 [Microsoft. SharePoint. SPRoleAssignment](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignment)

 [Microsoft. SharePoint. SPRoleAssignmentCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignmentCollection)

 [Microsoft. SharePoint. SPSecurableObject](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurableObject)

 [Microsoft. SharePoint. SPSecurity](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity)

 [Microsoft. SharePoint. SPSite](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite)

 [Microsoft. SharePoint. SPUser](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPUser)

 [Microsoft. SharePoint. SPUserCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPUserCollection)

 [Microsoft. SharePoint. SPView](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPView)

 [Microsoft. SharePoint. SPViewCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewCollection)

 [Microsoft. SharePoint. SPViewContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewContext)

 [Microsoft. SharePoint. SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb)

 [Microsoft. SharePoint. SPWebCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWebCollection)

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="see-also"></a>Viz také
 Testování [částí kódu](../test/unit-test-your-code.md) [testování aplikací SharePoint 2010 pomocí programových testů uživatelského rozhraní](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md) [testování výkonu webu a zátěžových testů pro aplikace SharePoint 2010 a 2013](https://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54) [vývoj řešení služby SharePoint](https://msdn.microsoft.com/library/059bce0f-c301-4234-a0b4-9c14b7cdfa3e)
