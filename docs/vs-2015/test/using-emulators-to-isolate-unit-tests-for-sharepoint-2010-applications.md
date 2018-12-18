---
title: Izolace testů jednotek aplikací pro Sharepoint 2010 pomocí emulátorů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b681164c-c87a-4bd7-be48-ed77e1578471
caps.latest.revision: 17
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4c2922d5be6c3326dac3b0c2667e5210ec908722
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915448"
---
# <a name="using-emulators-to-isolate-unit-tests-for-sharepoint-2010-applications"></a>Izolace testů jednotek aplikací pro SharePoint 2010 s použitím emulátorů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Balíček Microsoft.SharePoint.Emulators obsahuje sadu knihoven, které vám pomohou vytvořit samostatné testy jednotky pro aplikace Microsoft SharePoint 2010. Emulátory používají [překrytí](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) z [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) izolačního k vytvoření jednoduché objektů v paměti, které napodobují nejčastěji používané objekty a metody rozhraní API služby SharePoint. Pokud metoda služby SharePoint není emulována nebo pokud chcete změnit výchozí chování emulátoru, můžete vytvořit falešné ovladače překrytí k poskytnutí požadovaných výsledků.  
  
 Stávající testovací metody a třídy lze snadno převést na spouštění v kontextu emulátoru. Tato funkce umožňuje vytvářet testy dvojího užití. Test dvojího užití může přepínat mezi zkouškami integrace oproti skutečnému rozhraní API služby SharePoint a izolovanými jednotkami testování, které používají emulátory.  
  
##  <a name="BKMK_In_this_topic"></a> V tomto tématu  
 [Požadavky](#BKMK_Requirements)  
  
 [Příklad AppointmentsWebPart](#BKMK_The_AppointmentsWebPart_example)  
  
 [Převod existujícího testu](#BKMK_Converting_an_existing_test)  
  
- [Přidání balíčku emulátorů do projektu testů](#BKMK_Adding_the_Emulators_package_to_a_test_project)  
  
- [Spustí metodu testu s emulací](#BKMK__Running_a_test_method_in_the_emulation_context)  
  
  [Vytváření dvojího užití třídy a metody](#BKMK_Creating_dual_use_classes_and_methods)  
  
  [Pomocí TestInitialize a TestCleanup atributy k vytvoření dvojího užití třídu testu](#BKMK_Using_TestInitialize_and_TestCleanup_attributes_to_create_a_dual_use_test_class)  
  
  [Zpracování neemulovaných metod služby SharePoint](#BKMK_Handling_non_emulated_SharePoint_methods)  
  
  [Psaní testů emulace od začátku a souhrn](#BKMK_Writing_emulation_tests_from_scratch__and_a_summary)  
  
  [Příklad](#BKMK_Example)  
  
  [Emulované typů služby SharePoint](#BKMK_Emulated_SharePoint_types)  
  
##  <a name="BKMK_Requirements"></a> Požadavky  
  
- Microsoft SharePoint 2010 (SharePoint 2010 Server nebo SharePoint 2010 Foundation)  
  
- Microsoft Visual Studio Enterprise  
  
- Balíček NuGet pro emulátory Microsoft SharePoint  
  
  Také by měl být obeznámeni s [základy testování jednotek v sadě Visual Studio](../test/unit-test-basics.md) a mít základní znalost [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
##  <a name="BKMK_The_AppointmentsWebPart_example"></a> Příklad AppointmentsWebPart  
 AppointmentsWebPart vám umožňuje zobrazit a spravovat seznam schůzek služby SharePoint.  
  
 ![Události webovou část](../test/media/ut-emulators-appointmentswebpart.png "UT_EMULATORS_AppointmentsWebPart")  
  
 V tomto příkladu otestujeme dvě metody webové části:  
  
- `ScheduleAppointment` Metoda ověřuje hodnoty položky seznamu předané do metody a vytvoří novou položku v seznamu na zadaném webu služby SharePoint.  
  
- `GetAppointmentsForToday` Metoda vrátí podrobnosti o dnešních schůzkách.  
  
  [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Converting_an_existing_test"></a> Převod existujícího testu  
 V typickém testu metody v součásti služby SharePoint testovací metoda vytvoří dočasný web SharePoint Foundation a přidá komponenty SharePoint na web, který testovaný kód vyžaduje. Zkušební metoda pak vytvoří a uplatní instanci komponenty. Na konci testu nastavení je web protržen.  
  
 `ScheduleAppointment` Metoda našeho testovaného kódu je pravděpodobně jednou z prvních metod zapsaných pro komponentu:  
  
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
  
 První test funkčnosti v `ScheduleAppointment` metoda může vypadat třeba takto:  
  
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
  
 Přestože tato testovací metoda zkontroluje, zda `ScheduleAppointment` metoda správně přidá novou položku do seznamu, ale spíše o test integrace webové části než test specifického chování kódu. Vnější závislosti služby SharePoint a rozhraní API služby SharePoint může způsobit selhání jiných důvodů než uživatelský kód v testu `ScheduleAppointment` metody. Režie při vytváření a ničení webu SharePoint můžete také provést test příliš pomalé ke spuštění jako běžné součásti procesu kódování. Probíhá instalace a zničení webu pro každou zkušební metodu sloučeniny pouze problém s vytvářením testů jednotek pro vývojáře.  
  
 Emulátory Microsoft SharePoint poskytují sadu objektů a metod "dvojníků", které napodobují chování nejběžnější rozhraní API služby SharePoint. Emulované metody jsou nenáročné implementace rozhraní API služby SharePoint, které nevyžadují spuštění SharePoint. S použitím Microsoft Fakes můžete zkrátit volání rozhraní API služby SharePoint pro metodu zdvojnásobení z emulátorů SharePoint, izolace vašich testů a ujistěte se, že testujete kód, který chcete. Při volání metod služby SharePoint, které nejsou emulovány, můžete použít produkt Fakes přímo k vytvoření požadované chování.  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Adding_the_Emulators_package_to_a_test_project"></a> Přidání balíčku emulátorů do projektu testů  
 Přidání emulátorů SharePoint do testovacího projektu:  
  
1. V Průzkumníku řešení vyberte projekt testu.  
  
2. Zvolte **spravovat balíčky NuGet...**  v místní nabídce.  
  
3. Hledání **Online** kategorii pro `Microsoft.SharePoint.Emulators`a klikněte na tlačítko **nainstalovat**.  
  
   ![Balíček NuGet pro emulátory SharePoint](../test/media/ut-emulators-nuget.png "UT_EMULATORS_Nuget")  
  
   [V tomto tématu](#BKMK_In_this_topic)  
  
###  <a name="BKMK__Running_a_test_method_in_the_emulation_context"></a> Spustí metodu testu s emulací  
 Instalace balíčku přidává odkazy na požadované knihovny do vašich projektů. Chcete-li usnadnit používání emulátorů v existující třídě testu, přidejte obory názvů `Microsoft.SharePoint.Emulators` a `Microsoft.QualityTools.Testing.Emulators`.  
  
 Pokud chcete povolit emulaci testovacích metod, sbalte tělo metody v `using` příkaz, který vytvoří `SharePointEmulationScope` objektu. Příklad:  
  
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
  
 Při spuštění zkušební metody volá runtime emulátoru Microsoft Fakes na dynamické vložení kódu do metody služby SharePoint k rozdělení volání těchto metod na delegáty, kteří jsou deklarováni v knihovně Microsoft.SharePoint.Fakes.dll. Microsoft.SharePoint.Emulators.dll implementuje delegáty emulované metody a úzce tak napodobuje skutečné chování služby SharePoint. Když metoda testování nebo testovaná komponenta volá metodu SharePoint, je výsledné chování je chováním emulace.  
  
 ![Emulátor provádění toku](../test/media/ut-emulators-flowchart.png "UT_EMULATORS_FlowChart")  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Creating_dual_use_classes_and_methods"></a> Vytváření dvojího užití třídy a metody  
 Pokud chcete vytvořit metody, které lze použít pro oba testy integrace proti skutečným testům rozhraní API a izolovaným testům jednotky, které používají emulátory, použijte přetížený konstruktor `SharePointEmulationScope(EmulationMode)` ke sbalení kódu metody testování. Dvě hodnoty `EmulationMode` výčtu určit, zda rozsah používá emulátory (`EmulationMode.Enabled`) nebo zda rozsah používá rozhraní API služby SharePoint (`EmulationMode.Passthrough`).  
  
 Tady je například jak můžete upravit předchozí test pro dvojité použití:  
  
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
  
##  <a name="BKMK_Using_TestInitialize_and_TestCleanup_attributes_to_create_a_dual_use_test_class"></a> Pomocí TestInitialize a TestCleanup atributy k vytvoření dvojího užití třídu testu  
 Pokud spustíte všechny nebo většinu testů v třídy pomocí `SharePointEmulationScope`, můžete využít technik na úrovni třídy pro nastavení režimu emulace.  
  
- Třída testu, které se připisuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> můžete vytvořit a zničit obor.  
  
- Nastavení `EmulationMode` třída úroveň umožňuje automatizovat změny režimu mezi `EmulationMode.Enabled` a `EmulationMode.Passthrough`.  
  
  Metoda třídy s atributem `[TestInitialize]` se spouští na začátku každé zkušební metody a metody s atributem `[TestCleanup]` běží na konci jednotlivých zkušebních metod. Můžete deklarovat soukromé pole pro `SharePointEmulationScope` objekt na úrovni třídy, inicializovat jej v `TestInitialize` s metodou atributů a potom na objekt v `TestCleanup` s metodou atributů.  
  
  Můžete použít libovolnou metodu, kterou zvolíte pro automatizaci výběru `EmulationMode`. Jedním ze způsobů je zkontrolovat existenci symbolu pomocí direktiv preprocesoru. Například pokud chcete spustit testovací metody ve třídě pomocí emulátorů, můžete definovat symbol, jako `USE_EMULATION` v testovacím souboru projektu nebo na příkazovém řádku sestavení. Pokud je definován symbol úrovni třídy `EmulationMode` – konstanta je deklarovaný a nastavena na `Enabled`. V opačném případě je konstanta nastavena na `Passthrough`.  
  
  Tady je příklad testovací třídy, která demonstruje použití direktiv preprocesoru a `TestInitialize` a `TestCleanup` s atributy metody pro nastavení režimu emulace.  
  
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
  
##  <a name="BKMK_Handling_non_emulated_SharePoint_methods"></a> Zpracování neemulovaných metod služby SharePoint  
 Ne všechny typy služby SharePoint jsou emulované, a ne všechny metody v některých emulovaných typech jsou emulované. Pokud kód zkoušeného volá metody služby SharePoint, která není emulována, vyvolá metoda `NotSupportedException` výjimky. Když dojde k výjimce, přidáte objekt překrytí napodobeniny metody služby SharePoint.  
  
 **Nastavení falešných prvků Sharepoint**  
  
 Chcete-li explicitně volat Překryvné ovladače Microsoft Fakes:  
  
1. Pokud chcete překrýt třídu služby SharePoint, která není emulována, upravte soubor Microsoft.SharePoint.fakes a přidejte třídu do seznamu překrytých tříd. Zobrazit [konfigurace generování kódu ze zástupných procedur a překrytí](http://msdn.microsoft.com/library/hh708916.aspx#bkmk_configuring_code_generation_of_stubs) část [vytváření, kompilace a konvence pojmenování ve Microsoft Fakes kódu](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md).  
  
    ![Napodobeniny složku v Průzkumníku řešení](../test/media/ut-emulators-fakesfilefolder.png "UT_EMULATORS_FakesFileFolder")  
  
2. Znovu sestavte testovací alespoň jednou po instalaci balíčku Microsoft SharePoint Emulators, a pokud jste upravili soubor Microsoft.SharePoint.Fakes. Vytváření projektu vytvoří a naplní **FakesAssembly** složky v kořenové složce projektu na disku.  
  
    ![Složka FakesAssembly](../test/media/ut-emulators-fakesassemblyfolder.png "UT_EMULATORS_FakesAssemblyFolder")  
  
3. Přidejte odkaz na **Microsoft.SharePoint.14.0.0.0.Fakes.dll** sestavení, které se nachází v **FakesAssembly** složky.  
  
4. (Volitelné) Přidejte direktivu oboru názvů pro třídu testu pro `Microsoft.QualityTools.Testing.Fakes`, `Microsoft.SharePoint.Fakes` a všechny vnořené obory názvů `Microsoft.SharePoint.Fakes`, kterou chcete použít.  
  
   **Implementace delegáta překrytí pro metodu služby SharePoint**  
  
   V našem vzorovém projektu `GetAppointmentsForToday` volání metod [SPList.GetItems(SPQuery)](http://msdn.microsoft.com/library/ms457534.aspx) metoda API služby SharePoint.  
  
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
  
 `SPList.GetItems(SPQuery)` Přetížené verze `GetItems` metoda není emulována. Proto pouhé obtečení existujícího testu `GetAppointmentsForToday` v `SharePoint.Emulation.Scope` selže. Pokud chcete vytvořit pracovní test, musíte napsat implementaci delegáta Fakes `ShimSPList.GetItemsSPQuery` , který vrátí výsledky, které chcete pro porovnání výsledků testů.  
  
 Zde je úprava stávající testovací metody, `GetAppointmentsForTodayReturnsOnlyTodaysAppointments`, která implementuje delegáta napodobeniny. Požadované změny jsou uvedeny v komentářích:  
  
> [!IMPORTANT]
>  Testovací metody, které explicitně vytvoří throw Překryvné ovladače Fakes `ShimNotSupported` při spuštění testu došlo k výjimce `EmulationMode.Passthrough` kontextu. K tomuto problému vyhnout, použijte proměnnou nastavit `EmulationMode` hodnotu a zalomení některých kódů Fakes v `if` příkaz, který testuje hodnotu.  
  
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
  
 V této metodě nejprve otestujete, že je povolena možnost emulace. Pokud se jedná, vytvoříme objekt překrytí napodobeniny pro náš `SPList` seznamu a pak vytvořit a přiřadíme metodu na jeho `GetItemsSPQuery` delegovat. Delegát používá Fakes `Bind` metoda pro přidání správné položky seznamu na `ShimSPListItemCollection` , který je vrácen volajícímu.  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Writing_emulation_tests_from_scratch__and_a_summary"></a> Psaní testů emulace od začátku a souhrn  
 Přestože techniky k vytvoření emulace a testů dvojího užití, které jsou popsané v předchozí části se předpokládá, že převádíte stávající testy, můžete také použít techniky pro psaní testů od začátku. Následující seznam obsahuje souhrn těchto technik:  
  
- Chcete-li v testovacím projektu použít emulátory, přidejte do projektu balíček Microsoft.SharePoint.Emulators NuGet.  
  
- Chcete-li použít emulátory v testovací metodě, vytvořte `SharePointEmulationScope` objekt na začátek metody. Všechny podporované rozhraní API služby SharePoint budou emulována, dokud nebude obor vyřazen.  
  
- Napište kód testu, jako kdyby kdybyste psali proti skutečnému rozhraní API služby SharePoint. Kontext emulace automaticky přesměruje volání metody SharePoint pro svých emulátorů.  
  
- Ne všechny objekty služby SharePoint jsou emulované, a ne všechny metody některých emulované objektů jsou emulované. A `NotSupportedException` výjimka je vyvolána při použití neemulovaného objektu nebo metody. V takovém případě explicitně vytvořte delegáta překrytí napodobeniny metody k vrátila požadované chování.  
  
- Chcete-li vytvořit testy dvojího užití, použijte `SharePointEmulationScope(EmulationMode)` konstruktor pro vytvoření objektu rozsahu emulace. `EmulationMode` Hodnota určuje, zda jsou volání služby SharePoint emulované nebo spustit na skutečném webu SharePoint.  
  
- Pokud všechny nebo Většina metod testování v testovací třídě spustí kontext emulace, můžete použít úroveň třídy `TestInitialize` s metodou atributů pro vytvoření `SharePointEmulationScope` objektu a pole úrovni třídy pro nastavení režimu emulace. To vám pomůže automatizovat změny režimu emulace. Potom použijte `TestCleanup` s metodou atributů pro uvolnění objektu oboru.  
  
  [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Example"></a> Příklad  
 Zde je poslední příklad, který zahrnuje techniky emulace služby SharePoint, které jsou popsané výše:  
  
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
  
##  <a name="BKMK_Emulated_SharePoint_types"></a> Emulované typů služby SharePoint  
 [Microsoft.SharePoint.SPField](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPField)  
  
 [Microsoft.SharePoint.SPFieldIndex](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndex)  
  
 [Microsoft.SharePoint.SPFieldIndexCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndexCollection)  
  
 [Microsoft.SharePoint.SPFieldLink](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLink)  
  
 [Microsoft.SharePoint.SPFieldLinkCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLinkCollection)  
  
 [Microsoft.SharePoint.SPFieldUrlValue](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldUrlValue)  
  
 [Microsoft.SharePoint.SPFile](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFile)  
  
 [Microsoft.SharePoint.SPFileCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFileCollection)  
  
 [Microsoft.SharePoint.SPFolder](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolder)  
  
 [Microsoft.SharePoint.SPFolderCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolderCollection)  
  
 [Microsoft.SharePoint.SPItem](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPItem)  
  
 [Microsoft.SharePoint.SPItemEventDataCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventDataCollection)  
  
 [Microsoft.SharePoint.SPItemEventProperties](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventProperties)  
  
 [Microsoft.SharePoint.SPList](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPList)  
  
 [Microsoft.SharePoint.SPListCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListCollection)  
  
 [Microsoft.SharePoint.SPListEventProperties](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListEventProperties)  
  
 [Microsoft.SharePoint.SPListItem](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItem)  
  
 [Microsoft.SharePoint.SPListItemCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItemCollection)  
  
 [Microsoft.SharePoint.SPQuery](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPQuery)  
  
 [Microsoft.SharePoint.SPRoleAssignment](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignment)  
  
 [Microsoft.SharePoint.SPRoleAssignmentCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignmentCollection)  
  
 [Microsoft.SharePoint.SPSecurableObject](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurableObject)  
  
 [Microsoft.SharePoint.SPSecurity](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity)  
  
 [Microsoft.SharePoint.SPSite](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite)  
  
 [Microsoft.SharePoint.SPUser](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPUser)  
  
 [Microsoft.SharePoint.SPUserCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPUserCollection)  
  
 [Microsoft.SharePoint.SPView](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPView)  
  
 [Microsoft.SharePoint.SPViewCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewCollection)  
  
 [Microsoft.SharePoint.SPViewContext](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewContext)  
  
 [Microsoft.SharePoint.SPWeb](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb)  
  
 [Microsoft.SharePoint.SPWebCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPWebCollection)  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Viz také  
 [Testování částí kódu](../test/unit-test-your-code.md)   
 [Testování aplikací pro SharePoint 2010 pomocí programových testů uživatelského rozhraní](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)   
 [Testování výkonnosti webů a zátěžové testování aplikací SharePoint 2010 a 2013](http://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54)   
 [Vývoj řešení služby SharePoint](http://msdn.microsoft.com/library/059bce0f-c301-4234-a0b4-9c14b7cdfa3e)



