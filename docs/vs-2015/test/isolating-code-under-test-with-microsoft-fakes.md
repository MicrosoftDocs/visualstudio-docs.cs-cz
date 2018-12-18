---
title: Izolace testovaného kódu pomocí rozhraní Microsoft Fakes | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a03c2e83-a41f-4854-bcf2-fcaa277a819d
caps.latest.revision: 18
ms.author: gewarren
manager: douge
ms.openlocfilehash: a2c5806af5712a396659d484d09d3fd7374111a1
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220928"
---
# <a name="isolating-code-under-test-with-microsoft-fakes"></a>Izolace testovaného kódu pomocí zástupného rozhraní Microsoft
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft Fakes může pomoci izolovat testovaný nahrazením ostatních částí aplikace pomocí kód *zástupné procedury* nebo *překrytí*. Jedná se o malé části kódu, které jsou pod kontrolou testů. Díky izolaci testovacího kódu víte, že pokud se test nezdaří, příčina je zde a ne někde jinde. Zástupné procedury a překrytí také umožňují testování kódu, i když jiné části aplikace ještě nefungují.  
  
 Jsou dva typy napodobenin:  
  
- A [se zakázaným inzerováním](#stubs) nahradí třídu malou náhradou, která implementuje stejné rozhraní.  Pro použití zástupných procedur je nutné navrhnout aplikaci tak, aby jednotlivé součásti závisely pouze na rozhraních a nikoli na ostatních součástech. („Součást“ představuje třídu nebo skupinu tříd, které jsou navrženy a aktualizovány společně a obvykle obsaženy v sestavení.)  
  
- A [překrytí](#shims) upravuje zkompilovaný kód aplikace v době běhu, takže místo volání určené metody spustí kód překrytí, vaším testem. Překrytí lze použít pro nahrazení volání do sestavení, která nelze upravit (např. sestavení .NET).  
  
  ![Napodobeniny nahradit další součásti](../test/media/fakes-2.png "Fakes-2")  
  
  **Požadavky**  
  
- Visual Studio Enterprise  
  
## <a name="choosing-between-stub-and-shim-types"></a>Volba mezi zástupnou procedurou a překrytím  
 Obvykle byste měli považovat projekt sady Visual Studio za součást, protože vytváříte a aktualizujete tyto třídy současně. Měli byste zvážit použití zástupných procedur a překrytí pro volání, která projekt provádí do jiných projektů v rámci vašeho řešení nebo do jiných sestavení, na která projekt odkazuje.  
  
 Jako obecné vodítko použijte zástupné procedury pro volání v rámci řešení sady Visual Studio a překrytí použijte pro volání do jiných odkazovaných sestavení. Je to proto, že u vašeho vlastního řešení je vhodné oddělit součásti definováním rozhraní tak, jak vyžaduje vytváření zástupných procedur. Ale externí sestavení, jako například System.dll, nejsou obvykle vybavena samostatnými definicemi rozhraní, takže je nutné místo toho použít překrytí.  
  
 Ostatní úvahy:  
  
 **Výkon.** Překrytí pracují pomaleji, protože přepisují kód za běhu. Zástupné procedury nemají takové nároky na výkon a jsou stejně rychlé jako virtuální metody.  
  
 **Statické metody, zapečetěné typy.** Zástupné procedury můžete použít pouze k implementaci rozhraní. Proto nelze použít typy zástupných procedur pro statické metody, nevirtuální metody, zapečetěné virtuální metody, metody v zapečetěných typech atd.  
  
 **Vnitřní typy.** Zástupné procedury i překrytí lze použít s vnitřními typy, které jsou přístupné pomocí atributu sestavení <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.  
  
 **Privátní metody.** Překrytí mohou nahradit volání do soukromých metod, pokud jsou viditelné všechny typy v podpisu metody. Zástupné procedury mohou nahradit pouze viditelné metody.  
  
 **Rozhraní a abstraktní metody.** Zástupné procedury poskytují implementace rozhraní a abstraktní metody, které lze použít při testování. Překrytí nemohou využít rozhraní a abstraktní metody, protože nedisponují těly metody.  
  
 Obecně doporučujeme používat typy zástupných procedur k izolaci od závislostí v rámci vašeho základu kódu. To lze provést skrytím součástí za rozhraní. Typy překrytí lze použít k izolaci od součástí třetích stran, které neposkytují testovatelné rozhraní API.  
  
##  <a name="stubs"></a> Začínáme se zástupnými procedurami  
 Podrobnější popis najdete v tématu [pomocí zástupných procedury k izolování částí aplikace pro testování částí od sebe navzájem](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).  
  
1.  **Vložení rozhraní**  
  
     Chcete-li použít zástupné procedury, musíte kód, který chcete otestovat, napsat takovým způsobem, aby explicitně nezmiňoval třídy v jiné součásti aplikace. „Součást“ představuje třídu nebo třídy, které jsou vyvíjeny a aktualizovány společně a obvykle jsou obsaženy v jednom projektu sady Visual Studio. Proměnné a parametry by měly být deklarovány pomocí rozhraní a instance ostatních součástí by měly být předány nebo vytvořeny pomocí továrny. Například pokud je součást StockFeed třídou v jiné součásti aplikace, pak toto bude považováno za chybné:  
  
     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`  
  
     Namísto toho definujte rozhraní, které lze implementovat jinou součástí a které může být také implementováno pomocí zástupné procedury pro testovací účely:  
  
    ```csharp  
    public int GetContosoPrice(IStockFeed feed)  
    { return feed.GetSharePrice("COOO"); }  
  
    ```  
  
    ```vb  
    Public Function GetContosoPrice(feed As IStockFeed) As Integer  
     Return feed.GetSharePrice("COOO")  
    End Function  
  
    ```  
  
2.  **Přidání napodobenin sestavení**  
  
    1.  V Průzkumníku řešení rozbalte seznam odkazů testového projektu. Pokud pracujete v jazyce Visual Basic, musíte zvolit **zobrazit všechny soubory** Chcete-li zobrazit seznam odkazů.  
  
    2.  Vyberte odkaz na sestavení, ve kterém je definováno rozhraní (například IStockFeed). V místní nabídce tento odkaz, zvolte **přidat napodobeniny sestavení**.  
  
    3.  Znovu sestavte řešení.  
  
3.  Ve vašich testech vytvořte instance zástupné procedury a zadejte kód pro jeho metody:  
  
    ```csharp  
    [TestClass]  
    class TestStockAnalyzer  
    {  
        [TestMethod]  
        public void TestContosoStockPrice()  
        {  
          // Arrange:  
  
            // Create the fake stockFeed:  
            IStockFeed stockFeed =   
                 new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.  
                     {  
                         // Define each method:  
                         // Name is original name + parameter types:  
                         GetSharePriceString = (company) => { return 1234; }  
                     };  
  
            // In the completed application, stockFeed would be a real one:  
            var componentUnderTest = new StockAnalyzer(stockFeed);  
  
          // Act:  
            int actualValue = componentUnderTest.GetContosoPrice();  
  
          // Assert:  
            Assert.AreEqual(1234, actualValue);  
        }  
        ...  
    }  
    ```  
  
    ```vb  
    <TestClass()> _  
    Class TestStockAnalyzer  
  
        <TestMethod()> _  
        Public Sub TestContosoStockPrice()  
            ' Arrange:  
            ' Create the fake stockFeed:  
            Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed  
            With stockFeed  
                .GetSharePriceString = Function(company)  
                                           Return 1234  
                                       End Function  
            End With  
            ' In the completed application, stockFeed would be a real one:  
            Dim componentUnderTest As New StockAnalyzer(stockFeed)  
            ' Act:  
            Dim actualValue As Integer = componentUnderTest.GetContosoPrice  
            ' Assert:  
            Assert.AreEqual(1234, actualValue)  
        End Sub  
    End Class  
  
    ```  
  
     Zvláštní část kouzla tady je třída `StubIStockFeed`. Pro každé rozhraní v odkazovaném sestavení generuje mechanismus rozhraní Microsoft Fakes zástupnou třídu. Název zástupné třídy je odvozen od názvu rozhraní s "`Fakes.Stub`" jako předponu a připojenými parametry názvů typu.  
  
     Zástupné procedury jsou také generovány pro mechanismy získání a nastavení vlastností, pro události a pro obecné metody. Další informace najdete v tématu [pomocí zástupných procedury k izolování částí aplikace pro testování částí od sebe navzájem](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).  
  
##  <a name="shims"></a> Začínáme s překrytími  
 (Podrobnější popis najdete v tématu [izolace aplikace od ostatních sestavení pro testování částí pomocí Překryvné ovladače](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).)  
  
 Předpokládejme, že vaše komponenta obsahuje volání `DateTime.Now`:  
  
```csharp  
// Code under test:  
    public int GetTheCurrentYear()  
    {  
       return DateTime.Now.Year;  
    }  
  
```  
  
 Při testování chcete překrýt `Now` vlastnost, protože skutečná verze neprakticky vrací jinou hodnotu při každém volání.  
  
 Chcete-li použít překrytí, není nutné upravovat kód aplikace nebo jej zapsat určitým způsobem.  
  
1. **Přidání napodobenin sestavení**  
  
    V Průzkumníku řešení otevřete odkazy projektu testování částí a vyberte odkaz na sestavení, které obsahuje metodu, kterou chcete simulovat. V tomto příkladu `DateTime` třída je v **System.dll**.  Chcete-li zobrazit odkazy v projektu jazyka Visual Basic, zvolte **zobrazit všechny soubory**.  
  
    Zvolte **přidat napodobeniny sestavení**.  
  
2. **Vložení překrytí do ShimsContext**  
  
   ```csharp  
   [TestClass]  
   public class TestClass1  
   {   
           [TestMethod]  
           public void TestCurrentYear()  
           {  
               int fixedYear = 2000;  
  
               // Shims can be used only in a ShimsContext:  
               using (ShimsContext.Create())  
               {  
                 // Arrange:  
                   // Shim DateTime.Now to return a fixed date:  
                   System.Fakes.ShimDateTime.NowGet =   
                   () =>  
                   { return new DateTime(fixedYear, 1, 1); };  
  
                   // Instantiate the component under test:  
                   var componentUnderTest = new MyComponent();  
  
                 // Act:  
                   int year = componentUnderTest.GetTheCurrentYear();  
  
                 // Assert:   
                   // This will always be true if the component is working:  
                   Assert.AreEqual(fixedYear, year);  
               }  
           }  
   }  
  
   ```  
  
   ```vb  
   <TestClass()> _  
   Public Class TestClass1  
       <TestMethod()> _  
       Public Sub TestCurrentYear()  
           Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()  
               Dim fixedYear As Integer = 2000  
               ' Arrange:  
               ' Detour DateTime.Now to return a fixed date:  
               System.Fakes.ShimDateTime.NowGet = _  
                   Function() As DateTime  
                       Return New DateTime(fixedYear, 1, 1)  
                   End Function  
  
               ' Instantiate the component under test:  
               Dim componentUnderTest = New MyComponent()  
               ' Act:  
               Dim year As Integer = componentUnderTest.GetTheCurrentYear  
               ' Assert:   
               ' This will always be true if the component is working:  
               Assert.AreEqual(fixedYear, year)  
           End Using  
       End Sub  
   End Class  
   ```  
  
    Názvy tříd překrytí jsou tvořeny vložením prefixu `Fakes.Shim` k původnímu názvu typu. Názvy parametrů jsou připojeny k názvu metody. (Není nutné přidat odkaz na System.Fakes žádné sestavení.)  
  
   Předchozí příklad používá překrytí pro statickou metodu. Chcete-li použít překrytí pro metodu instance, napište `AllInstances` mezi název typu a název metody:  
  
```  
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...  
```  
  
 (Neexistuje žádné sestavení 'System.IO.Fakes' Chcete-li odkazovat. Obor názvů je generován v procesu vytváření překrytí. Ale můžete použít "pomocí" nebo "Import" obvyklým způsobem.)  
  
 Můžete také vytvořit překrytí pro konkrétní instance, konstruktory a vlastnosti. Další informace najdete v tématu [izolace aplikace od ostatních sestavení pro testování částí pomocí Překryvné ovladače](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vzájemná izolace částí aplikace pomocí zástupných procedury za účelem testování jednotek](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)  
  
 [Izolace aplikace od ostatních sestavení pomocí překrytí za účelem testování jednotek](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)  
  
 [Vytváření, kompilace a konvence pojmenování kódu v Napodobeniny Microsoft](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)



