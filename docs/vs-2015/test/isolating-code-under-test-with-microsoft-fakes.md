---
title: Izolace testovaného kódu s napodobeninami společnosti Microsoft | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a03c2e83-a41f-4854-bcf2-fcaa277a819d
caps.latest.revision: 18
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c272906aa402c124b98e6b9f5556d8c825ee963
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660479"
---
# <a name="isolating-code-under-test-with-microsoft-fakes"></a>Izolace testovaného kódu pomocí zástupného rozhraní Microsoft
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Napodobeniny společnosti Microsoft vám pomohou izolovat testovaný kód nahrazením jiných částí aplikace pomocí zástupných *procedur* nebo *překrytí*. Jedná se o malé části kódu, které jsou pod kontrolou testů. Díky izolaci testovacího kódu víte, že pokud se test nezdaří, příčina je zde a ne někde jinde. Zástupné procedury a překrytí také umožňují testování kódu, i když jiné části aplikace ještě nefungují.

 Jsou dva typy napodobenin:

- [Zástupné procedury](#stubs) nahradí třídu malou náhradou, která implementuje stejné rozhraní.  Pro použití zástupných procedur je nutné navrhnout aplikaci tak, aby jednotlivé součásti závisely pouze na rozhraních a nikoli na ostatních součástech. („Součást“ představuje třídu nebo skupinu tříd, které jsou navrženy a aktualizovány společně a obvykle obsaženy v sestavení.)

- [Překrytí](#shims) upravuje zkompilovaný kód vaší aplikace za běhu, takže namísto provedení zadaného volání metody spustí kód překrytí, který váš test poskytuje. Překrytí lze použít pro nahrazení volání do sestavení, která nelze upravit (např. sestavení .NET).

  ![Napodobeniny nahrazují jiné součásti](../test/media/fakes-2.png "Napodobeniny – 2")

  **Požadavky**

- Visual Studio Enterprise

## <a name="choosing-between-stub-and-shim-types"></a>Volba mezi zástupnou procedurou a překrytím
 Obvykle byste měli považovat projekt sady Visual Studio za součást, protože vytváříte a aktualizujete tyto třídy současně. Měli byste zvážit použití zástupných procedur a překrytí pro volání, která projekt provádí do jiných projektů v rámci vašeho řešení nebo do jiných sestavení, na která projekt odkazuje.

 Jako obecné vodítko použijte zástupné procedury pro volání v rámci řešení sady Visual Studio a překrytí použijte pro volání do jiných odkazovaných sestavení. Je to proto, že u vašeho vlastního řešení je vhodné oddělit součásti definováním rozhraní tak, jak vyžaduje vytváření zástupných procedur. Ale externí sestavení, jako například System.dll, nejsou obvykle vybavena samostatnými definicemi rozhraní, takže je nutné místo toho použít překrytí.

 Ostatní úvahy:

 **Předepsané.** Překrytí pracují pomaleji, protože přepisují kód za běhu. Zástupné procedury nemají takové nároky na výkon a jsou stejně rychlé jako virtuální metody.

 **Statické metody, zapečetěné typy.** Zástupné procedury můžete použít pouze k implementaci rozhraní. Proto nelze použít typy zástupných procedur pro statické metody, nevirtuální metody, zapečetěné virtuální metody, metody v zapečetěných typech atd.

 **Interní typy.** Zástupné procedury i překrytí lze použít s vnitřními typy, které jsou zpřístupněny pomocí atributu Assembly <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.

 **Soukromé metody.** Překrytí mohou nahradit volání do soukromých metod, pokud jsou viditelné všechny typy v podpisu metody. Zástupné procedury mohou nahradit pouze viditelné metody.

 **Rozhraní a abstraktní metody.** Zástupné procedury poskytují implementace rozhraní a abstraktní metody, které lze použít při testování. Překrytí nemohou využít rozhraní a abstraktní metody, protože nedisponují těly metody.

 Obecně doporučujeme používat typy zástupných procedur k izolaci od závislostí v rámci vašeho základu kódu. To lze provést skrytím součástí za rozhraní. Typy překrytí lze použít k izolaci od součástí třetích stran, které neposkytují testovatelné rozhraní API.

## <a name="stubs"></a>Začínáme se zástupnými kódy
 Podrobnější popis najdete v tématu použití zástupných [procedur k izolaci částí vaší aplikace od sebe navzájem pro testování jednotek](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

1. **Rozhraní pro vložení**

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

2. **Přidat napodobeniny sestavení**

    1. V Průzkumníku řešení rozbalte seznam odkazů testového projektu. Pokud pracujete v Visual Basic, musíte zvolit možnost **Zobrazit všechny soubory** , aby se zobrazil seznam odkazů.

    2. Vyberte odkaz na sestavení, ve kterém je definováno rozhraní (například IStockFeed). V místní nabídce tohoto odkazu vyberte možnost **Přidat napodobeniny sestavení**.

    3. Znovu sestavte řešení.

3. Ve vašich testech vytvořte instance zástupné procedury a zadejte kód pro jeho metody:

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

     Speciální část Magic je `StubIStockFeed` třídy. Pro každé rozhraní v odkazovaném sestavení generuje mechanismus rozhraní Microsoft Fakes zástupnou třídu. Název třídy zástupné procedury je odvozen z názvu rozhraní, s "`Fakes.Stub`" jako předponou a s připojenými názvy typů parametrů.

     Zástupné procedury jsou také generovány pro mechanismy získání a nastavení vlastností, pro události a pro obecné metody. Další informace najdete v tématu použití zástupných [procedur k izolaci částí aplikace od sebe navzájem pro testování jednotek](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

## <a name="shims"></a>Začínáme s překrytím
 (Podrobnější popis naleznete v tématu [použití překrytí k izolaci aplikace od jiných sestavení pro testování částí](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).)

 Předpokládejme, že vaše komponenta obsahuje volání `DateTime.Now`:

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }

```

 Během testování byste chtěli překrýt vlastnost `Now`, protože reálná verze nezpůsobuje, že při každém volání vrátí jinou hodnotu.

 Chcete-li použít překrytí, není nutné upravovat kód aplikace nebo jej zapsat určitým způsobem.

1. **Přidat napodobeniny sestavení**

    V Průzkumníku řešení otevřete odkazy projektu testování částí a vyberte odkaz na sestavení, které obsahuje metodu, kterou chcete simulovat. V tomto příkladu je třída `DateTime` v **System. dll**.  Chcete-li zobrazit odkazy v projektu Visual Basic, vyberte možnost **Zobrazit všechny soubory**.

    Vyberte možnost **Přidat napodobeniny sestavení**.

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

    Názvy tříd překrytí jsou vytvářeny pomocí předpony `Fakes.Shim` původnímu názvu typu. Názvy parametrů jsou připojeny k názvu metody. (Nemusíte přidávat odkaz na sestavení do System. napodobeniny.)

   Předchozí příklad používá překrytí pro statickou metodu. Chcete-li použít překrytí pro metodu instance, napište `AllInstances` mezi název typu a název metody:

```
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

 (Pro referenci neexistuje žádné sestavení System. IO. falešného typu. Obor názvů je vygenerován procesem vytvoření překrytí. Ale můžete použít "using" nebo "Import" obvyklým způsobem.)

 Můžete také vytvořit překrytí pro konkrétní instance, konstruktory a vlastnosti. Další informace naleznete v tématu [použití překrytí k izolaci aplikace od jiných sestavení pro testování částí](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="in-this-section"></a>V tomto oddílu
 [Vzájemná izolace částí aplikace pomocí zástupných procedury za účelem testování jednotek](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

 [Izolace aplikace od ostatních sestavení pomocí překrytí za účelem testování jednotek](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

 [Vytváření, kompilace a konvence pojmenování kódu v Napodobeniny Microsoft](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
