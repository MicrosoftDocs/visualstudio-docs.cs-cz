---
title: Izolace testovaného kódu pomocí zástupného rozhraní Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- VB
- CSharp
ms.openlocfilehash: 662a61bf97e1726892b877dc79a0ef98340a34ec
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566888"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Izolace testovaného kódu pomocí Napodobenin Microsoft

Microsoft Fakes pomáhá izolovat kód, který testujete nahrazením jiných částí aplikace *se zástupnými kódy* nebo *podložkami*. Jedná se o malé části kódu, které jsou pod kontrolou testů. Díky izolaci testovacího kódu víte, že pokud se test nezdaří, příčina je zde a ne někde jinde. Zástupné procedury a překrytí také umožňují testování kódu, i když jiné části aplikace ještě nefungují.

Jsou dva typy napodobenin:

- [Se zakázaným inzerováním](#get-started-with-stubs) nahradí třídu malou náhradou, která implementuje stejné rozhraní.  Pro použití zástupných procedur je nutné navrhnout aplikaci tak, aby jednotlivé součásti závisely pouze na rozhraních a nikoli na ostatních součástech. („Součást“ představuje třídu nebo skupinu tříd, které jsou navrženy a aktualizovány společně a obvykle obsaženy v sestavení.)

- [Překrytí](#get-started-with-shims) upraví zkompilovaný kód aplikace za běhu tak, aby namísto volání zadané metody spustí kód překrytí, který poskytuje test. Překrytí lze nahradit volání sestavení, která nelze změnit, například sestavení .NET.

![Padělky nahradit jiné komponenty](../test/media/fakes-2.png)

**Požadavky**

- Visual Studio Enterprise
- Projekt rozhraní .NET Framework

> [!NOTE]
> - Standardní projekty .NET nejsou podporovány.
> - Profilování pomocí sady Visual Studio není k dispozici pro testy, které používají microsoft fakes.

## <a name="choose-between-stub-and-shim-types"></a>Výběr mezi typy se zakázaným inzerováním a překrytím
Obvykle byste měli považovat projekt sady Visual Studio za součást, protože vytváříte a aktualizujete tyto třídy současně. Měli byste zvážit použití zástupných procedur a překrytí pro volání, která projekt provádí do jiných projektů v rámci vašeho řešení nebo do jiných sestavení, na která projekt odkazuje.

Jako obecné vodítko použijte zástupné procedury pro volání v rámci řešení sady Visual Studio a překrytí použijte pro volání do jiných odkazovaných sestavení. Je to proto, že u vašeho vlastního řešení je vhodné oddělit součásti definováním rozhraní tak, jak vyžaduje vytváření zástupných procedur. Ale externí sestavení, jako je *System.dll* obvykle nejsou k dispozici samostatné definice rozhraní, takže je nutné použít překrytí místo.

Ostatní úvahy:

**Výkon.** Překrytí pracují pomaleji, protože přepisují kód za běhu. Zástupné procedury nemají takové nároky na výkon a jsou stejně rychlé jako virtuální metody.

**Statické metody, zapečetěné typy.** Zástupné procedury můžete použít pouze k implementaci rozhraní. Proto nelze použít typy zástupných procedur pro statické metody, nevirtuální metody, zapečetěné virtuální metody, metody v zapečetěných typech atd.

**Vnitřní typy.** Zástupné procedury i překrytí lze použít s interními typy, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>které jsou přístupné pomocí atributu sestavení .

**Soukromé metody.** Překrytí mohou nahradit volání do soukromých metod, pokud jsou viditelné všechny typy v podpisu metody. Zástupné procedury mohou nahradit pouze viditelné metody.

**Rozhraní a abstraktní metody.** Zástupné procedury poskytují implementace rozhraní a abstraktní metody, které lze použít při testování. Překrytí nemůže instrumentovat rozhraní a abstraktní metody, protože nemají těla metod.

Obecně doporučujeme používat typy zástupných procedur k izolaci od závislostí v rámci vašeho základu kódu. To lze provést skrytím součástí za rozhraní. Typy překrytí lze použít k izolaci od součástí třetích stran, které neposkytují testovatelné rozhraní API.

## <a name="get-started-with-stubs"></a>Začínáme se zakázanými útržky
Podrobnější popis naleznete v [tématu Použití zástupných procedur k odsazení částí aplikace od sebe navzájem pro testování částí](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

1. **Vstřikovací rozhraní**

     Chcete-li použít zástupné procedury, musíte kód, který chcete otestovat, napsat takovým způsobem, aby explicitně nezmiňoval třídy v jiné součásti aplikace. „Součást“ představuje třídu nebo třídy, které jsou vyvíjeny a aktualizovány společně a obvykle jsou obsaženy v jednom projektu sady Visual Studio. Proměnné a parametry by měly být deklarovány pomocí rozhraní a instance ostatních součástí by měly být předány nebo vytvořeny pomocí továrny. Například pokud je součást StockFeed třídou v jiné součásti aplikace, pak toto bude považováno za chybné:

     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`

     Namísto toho definujte rozhraní, které lze implementovat jinou součástí a které může být také implementováno pomocí zástupné procedury pro testovací účely:

    ```csharp
    public int GetContosoPrice(IStockFeed feed) => feed.GetSharePrice("COOO");
    ```

    ```vb
    Public Function GetContosoPrice(feed As IStockFeed) As Integer
     Return feed.GetSharePrice("COOO")
    End Function

    ```

2. **Přidat falešná sestava**

    1. V **Průzkumníku řešení**rozbalte seznam odkazů testovacího projektu. Pokud pracujete v jazyce Visual Basic, musíte zvolit **Zobrazit všechny soubory,** abyste viděli seznam odkazů.

    2. Vyberte odkaz na sestavení, ve kterém je definováno rozhraní (například IStockFeed). V místní nabídce tohoto odkazu zvolte **Přidat sestavení padělků**.

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

    Zvláštní kousek magie zde `StubIStockFeed`je třída . Pro každé rozhraní v odkazovaném sestavení generuje mechanismus rozhraní Microsoft Fakes zástupnou třídu. Název třídy se zakázaným inzerováním je odvozen od`Fakes.Stub`názvu rozhraní s " " jako předponou a připojenými názvy typů parametrů.

    Zástupné procedury jsou také generovány pro mechanismy získání a nastavení vlastností, pro události a pro obecné metody. Další informace naleznete [v tématu Použití zástupných procedur k oddělení částí aplikace od sebe navzájem pro testování částí](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

## <a name="get-started-with-shims"></a>Začínáme s podložkami
(Podrobnější popis naleznete v tématu [Použití překrytí](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)aplikace od jiných sestavení pro testování částí .)

Předpokládejme, že `DateTime.Now`komponenta obsahuje volání :

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }
```

Během testování byste chtěli překrytí `Now` vlastnosti, protože skutečná verze nepohodlně vrátí jinou hodnotu při každém volání.

Chcete-li použít překrytí, není nutné upravovat kód aplikace nebo jej psát určitým způsobem.

1. **Přidat falešná sestava**

     V **Průzkumníku řešení**otevřete odkazy na projekt testování částí a vyberte odkaz na sestavení, které obsahuje metodu, kterou chcete zfalšovat. V tomto příkladu je třída v `DateTime` *souboru System.dll*.  Chcete-li zobrazit odkazy v projektu jazyka Visual Basic, zvolte **Zobrazit všechny soubory**.

     Zvolte **Přidat falešná sestava**.

2. **Vložení překrytí do kontextu ShimsContext**

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

    Názvy tříd překrytí jsou `Fakes.Shim` tvořeny předponou na původní název typu. Názvy parametrů jsou připojeny k názvu metody. (Není třeba přidávat žádné sestavení odkaz na System.Fakes.)

Předchozí příklad používá překrytí pro statickou metodu. Chcete-li použít překrytí pro `AllInstances` metodu instance, zapište mezi název typu a název metody:

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

(Neexistuje žádná sestava 'System.IO.Fakes', na které by bylo možné odkazovat. Obor názvů je generován procesem vytváření překrytí. Ale můžete použít 'pomocí' nebo 'Import' obvyklým způsobem.)

Můžete také vytvořit překrytí pro konkrétní instance, konstruktory a vlastnosti. Další informace naleznete [v tématu Použití překrytí izolovat aplikace z jiných sestavení pro testování částí](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="in-this-section"></a>V tomto oddílu
[Vzájemná izolace částí aplikace pomocí zástupných procedur za účelem testování jednotek](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

[Izolace aplikace od jiných sestavení pomocí testů shim za účelem testování jednotek](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

[Vytváření, kompilace a konvence pojmenování kódu v Napodobeniny Microsoft](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
