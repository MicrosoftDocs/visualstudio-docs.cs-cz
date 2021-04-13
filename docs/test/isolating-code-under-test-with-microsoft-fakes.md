---
title: Izolace testovaného kódu pomocí zástupného rozhraní Microsoft
description: Seznamte se s tím, jak Microsoft předstírá pomáhá izolovat testovaný kód nahrazením jiných částí aplikace pomocí zástupných procedur nebo překrytí.
ms.custom: SEO-VS-2020
ms.date: 06/03/2020
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- VB
- CSharp
ms.openlocfilehash: 8800116393df30df59b9fbe9544c1bbd0ee1bc18
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295647"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Izolace testovaného kódu pomocí Napodobenin Microsoft

Napodobeniny společnosti Microsoft pomáhají izolovat testovaný kód nahrazením jiných částí aplikace pomocí zástupných *procedur* nebo *překrytí*. Jedná se o malé části kódu, které jsou pod kontrolou testů. Díky izolaci testovacího kódu víte, že pokud se test nezdaří, příčina je zde a ne někde jinde. Zástupné procedury a překrytí také umožňují testování kódu, i když jiné části aplikace ještě nefungují.

Jsou dva typy napodobenin:

- [Zástupné procedury](#get-started-with-stubs) nahradí třídu malou náhradou, která implementuje stejné rozhraní.  Pro použití zástupných procedur je nutné navrhnout aplikaci tak, aby jednotlivé součásti závisely pouze na rozhraních a nikoli na ostatních součástech. („Součást“ představuje třídu nebo skupinu tříd, které jsou navrženy a aktualizovány společně a obvykle obsaženy v sestavení.)

- [Překrytí](#get-started-with-shims) upravuje zkompilovaný kód vaší aplikace za běhu, takže namísto provedení zadaného volání metody spustí kód překrytí, který váš test poskytuje. Překrytí lze použít k nahrazení volání sestavení, která nelze upravovat, například sestavení .NET.

![Napodobeniny nahrazují jiné součásti](../test/media/fakes-2.png)

**Požadavky**

- Visual Studio Enterprise
- .NET Framework projekt
::: moniker range=">=vs-2019"
- Podpora projektů pro .NET Core, .NET 5,0 a SDK je v sadě Visual Studio 2019 Update 6 předem zobrazená a ve výchozím nastavení je v Update 8 povolená. Další informace najdete v tématu [Microsoft předstírá pro projekty ve stylu .NET Core a SDK](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects).
::: moniker-end

> [!NOTE]
> - Profilování v aplikaci Visual Studio není k dispozici pro testy, které používají napodobeniny společnosti Microsoft.

## <a name="choose-between-stub-and-shim-types"></a>Zvolit mezi typy zástupných procedur a překrytí
Obvykle byste měli považovat projekt sady Visual Studio za součást, protože vytváříte a aktualizujete tyto třídy současně. Měli byste zvážit použití zástupných procedur a překrytí pro volání, která projekt provádí do jiných projektů v rámci vašeho řešení nebo do jiných sestavení, na která projekt odkazuje.

Jako obecné vodítko použijte zástupné procedury pro volání v rámci řešení sady Visual Studio a překrytí použijte pro volání do jiných odkazovaných sestavení. Je to proto, že u vašeho vlastního řešení je vhodné oddělit součásti definováním rozhraní tak, jak vyžaduje vytváření zástupných procedur. Ale externí sestavení, jako například *System.dll* obvykle nejsou k dispozici s oddělenými definicemi rozhraní, takže je nutné místo toho použít překrytí.

Ostatní úvahy:

**Předepsané.** Překrytí pracují pomaleji, protože přepisují kód za běhu. Zástupné procedury nemají takové nároky na výkon a jsou stejně rychlé jako virtuální metody.

**Statické metody, zapečetěné typy.** Zástupné procedury můžete použít pouze k implementaci rozhraní. Proto nelze použít typy zástupných procedur pro statické metody, nevirtuální metody, zapečetěné virtuální metody, metody v zapečetěných typech atd.

**Interní typy.** Zástupné procedury i překrytí lze použít s vnitřními typy, které jsou zpřístupněny pomocí atributu Assembly <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> .

**Soukromé metody.** Překrytí mohou nahradit volání do soukromých metod, pokud jsou viditelné všechny typy v podpisu metody. Zástupné procedury mohou nahradit pouze viditelné metody.

**Rozhraní a abstraktní metody.** Zástupné procedury poskytují implementace rozhraní a abstraktní metody, které lze použít při testování. Překrytí nemůžou instrumentovat rozhraní a abstraktní metody, protože nemají tělo metody.

Obecně doporučujeme používat typy zástupných procedur k izolaci od závislostí v rámci vašeho základu kódu. To lze provést skrytím součástí za rozhraní. Typy překrytí lze použít k izolaci od součástí třetích stran, které neposkytují testovatelné rozhraní API.

## <a name="get-started-with-stubs"></a>Začínáme s použitím zástupných procedur
Podrobnější popis najdete v tématu použití zástupných [procedur k izolaci částí vaší aplikace od sebe navzájem pro testování částí](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

1. **Rozhraní pro vložení**

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

2. **Přidat napodobeniny sestavení**

   1. V **Průzkumník řešení** 
       - Pro starší projekt .NET Framework (jiný styl než SDK) rozbalte uzel **odkazy** projektu testování jednotek.
       ::: moniker range=">=vs-2019"
       - Pro projekt, který cílí na .NET Framework, .NET Core nebo .NET 5,0, rozbalte uzel **závislosti** a vyhledejte sestavení, které chcete v rámci **sestavení**, **projektů** nebo **balíčků** falešné.
       ::: moniker-end
       - Pokud pracujete v Visual Basic, vyberte **Zobrazit všechny soubory** na panelu nástrojů **Průzkumník řešení** a zobrazte tak uzel **odkazy** .
   2. Vyberte sestavení, které obsahuje definice třídy, pro které chcete vytvořit překrytí. Například pokud chcete překrýt **data a času**, vyberte **System.dll**.

   3. V místní nabídce vyberte možnost **Přidat napodobeniny sestavení**.

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

    Speciální část Magic je třída `StubIStockFeed` . Pro každé rozhraní v odkazovaném sestavení generuje mechanismus rozhraní Microsoft Fakes zástupnou třídu. Název třídy zástupné procedury je odvozen z názvu rozhraní s `Fakes.Stub` předponou "" jako předpony a s připojenými názvy typů parametrů.

    Zástupné procedury jsou také generovány pro mechanismy získání a nastavení vlastností, pro události a pro obecné metody. Další informace najdete v tématu použití zástupných [procedur k izolaci částí vaší aplikace od sebe navzájem pro testování částí](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

## <a name="get-started-with-shims"></a>Začínáme s překrytím
(Podrobnější popis naleznete v tématu [použití překrytí k izolaci aplikace od jiných sestavení pro testování částí](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).)

Předpokládejme, že vaše komponenta obsahuje volání `DateTime.Now` :

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }
```

Během testování byste chtěli překrýt `Now` vlastnost, protože reálná verze nezpůsobuje, že při každém volání vrátí jinou hodnotu.

Chcete-li použít překrytí, není nutné upravovat kód aplikace ani zapisovat konkrétním způsobem.

1. **Přidat napodobeniny sestavení**

     V **Průzkumník řešení** otevřete odkazy projektu testování částí a vyberte odkaz na sestavení, které obsahuje metodu, kterou chcete nafalešné. V tomto příkladu `DateTime` je třída v *System.dll*.  Chcete-li zobrazit odkazy v projektu Visual Basic, vyberte možnost **Zobrazit všechny soubory**.

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

    Názvy tříd překrytí jsou vytvářeny pomocí předpony `Fakes.Shim` na původní název typu. Názvy parametrů jsou připojeny k názvu metody. (Nemusíte přidávat odkaz na sestavení do System. napodobeniny.)

Předchozí příklad používá překrytí pro statickou metodu. Chcete-li použít překrytí pro metodu instance, napište `AllInstances` mezi název typu a název metody:

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

(Pro referenci neexistuje žádné sestavení System. IO. falešného typu. Obor názvů je vygenerován procesem vytvoření překrytí. Ale můžete použít "using" nebo "Import" obvyklým způsobem.)

Můžete také vytvořit překrytí pro konkrétní instance, konstruktory a vlastnosti. Další informace naleznete v tématu [použití překrytí k izolaci aplikace od jiných sestavení pro testování částí](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="using-microsoft-fakes-in-the-ci"></a>Používání napodobenin společnosti Microsoft v CI

### <a name="microsoft-fakes-assembly-generation"></a>Generování sestavení napodobenin společnosti Microsoft
Vzhledem k tomu, že Microsoft napodobenin vyžaduje Visual Studio Enterprise, generování napodobenin sestavení vyžaduje, abyste vytvořili projekt pomocí [úlohy sestavení sady Visual Studio](/azure/devops/pipelines/tasks/build/visual-studio-build?view=azure-devops&preserve-view=true).

::: moniker range=">=vs-2019"
> [!NOTE]
> Alternativou k tomu je ověřit, zda jsou sestavení napodobenina do CI a používat [úlohu MSBuild](../msbuild/msbuild-task.md?view=vs-2019&preserve-view=true). Když to uděláte, musíte se ujistit, že máte odkaz na sestavení generovaného sestavení napodobeniny v testovacím projektu, podobně jako následující fragment kódu:

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <ItemGroup>
        <Reference Include="FakesAssemblies\System.Fakes.dll"/>
    </ItemGroup>
</Project>
```

Tento odkaz se musí přidat do ručně konkrétně projektů ve stylu sady SDK (.NET Core, .NET 5,0 a .NET Framework), protože jsme přesunuli na implicitní přidávání odkazů na sestavení do testovacího projektu. Pokud použijete tuto metodu, musíte zajistit, aby bylo sestavení napodobenin Aktualizováno při změně nadřazeného sestavení.
::: moniker-end

### <a name="running-microsoft-fakes-tests"></a>Spuštění testů napodobenin společnosti Microsoft
Pokud jsou sestavení napodobeniny od společnosti Microsoft přítomna v nakonfigurovaném `FakesAssemblies` adresáři (ve výchozím nastavení `$(ProjectDir)FakesAssemblies` ), můžete spustit testy pomocí [úlohy VSTest](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops&preserve-view=true).

::: moniker range=">=vs-2019"
Distribuované testování pomocí projektů [VSTest](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops&preserve-view=true) .NET Core a .NET 5,0, které využívají Microsoft napodobeniny, vyžaduje Visual Studio 2019 Update 9 Preview `20201020-06` a vyšší.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="transitioning-your-net-framework-test-projects-that-use-microsoft-fakes-to-sdk-style-net-framework-net-core-or-net-50-projects"></a>Přechod na .NET Framework testovacích projektů, které používají Microsoft napodobeniny k projektům .NET Framework, .NET Core nebo .NET 5,0 ve stylu sady SDK
Budete potřebovat minimální změny v .NET Framework nastavené pro Microsoft napodobeniny k přechodu na rozhraní .NET Core nebo .NET 5,0. Je třeba vzít v úvahu tyto případy:
- Pokud používáte vlastní šablonu projektu, je nutné zajistit, že se jedná o styl sady SDK a sestavení pro kompatibilní cílové rozhraní.
- Některé typy existují v různých sestaveních v .NET Framework a .NET Core/. NET 5,0 (například `System.DateTime` existují v nástroji `System` / `mscorlib` v .NET Framework a v `System.Runtime` rozhraní .NET Core a .NET 5,0) a v těchto scénářích potřebujete změnit sestavení, které falešným.
- Pokud máte odkaz na sestavení pro sestavení napodobenin a testovací projekt, může se zobrazit upozornění sestavení o chybějícím odkazu, který se podobá:
  ```
  (ResolveAssemblyReferences target) ->
  warning MSB3245: Could not resolve this reference. Could not locate the assembly "AssemblyName.Fakes". Check to make sure the assembly exists on disk.
  If this reference is required by your code, you may get compilation errors.
  ```
  Toto upozornění je způsobeno tím, že v důsledku nezbytných změn provedených v případě napodobenin generování lze ignorovat. Je možné se vyhnout odebráním odkazu na sestavení ze souboru projektu, protože je teď implicitně přidávají během sestavení.
::: moniker-end

## <a name="microsoft-fakes-support"></a>Podpora společnosti Microsoft pro napodobeniny 
### <a name="microsoft-fakes-in-older-projects-targeting-net-framework-non-sdk-style"></a>Společnost Microsoft předstírá ve starších projektech cílících na .NET Framework (jiný styl než SDK).
- Generování sestavení napodobenin společnosti Microsoft je podporováno v Visual Studio Enterprise 2015 a vyšších.
- Microsoft falešné testy můžou běžet se všemi dostupnými balíčky NuGet Microsoft. TestPlatform.
- Pokrytí kódu je podporováno pro projekty testů, které používají Microsoft napodobeniny v Visual Studio Enterprise 2015 a vyšších.

### <a name="microsoft-fakes-in-sdk-style-net-framework-net-core-and-net-50-projects"></a>Microsoft předstírá v projektech .NET Framework, .NET Core a .NET 5,0 ve stylu sady SDK
- Generování sestavení společnosti Microsoft je ve výchozím nastavení v Visual Studio Enterprise 2019 Update 6 a ve výchozím nastavení povoleno v Update 8.
- Microsoft předstírá testy pro projekty, které cílí na .NET Framework, můžou běžet se všemi dostupnými balíčky NuGet Microsoft. TestPlatform.
- Microsoft předstírá testy pro projekty, které cílí na .NET Core a .NET 5,0, můžou běžet s balíčky NuGet Microsoft. TestPlatform s verzemi [16.9.0-Preview-20210106-01](https://www.nuget.org/packages/Microsoft.TestPlatform/16.9.0-preview-20210106-01) a vyšší.
- Pokrytí kódu je podporováno pro projekty testů, které cílí na .NET Framework pomocí napodobenin společnosti Microsoft v Visual Studio Enterprise verze 2015 a vyšší.
- Podpora pokrytí kódu pro projekty testů cílené na .NET Core a .NET 5,0 s použitím napodobenin společnosti Microsoft je k dispozici v systému Visual Studio 2019 Update 9 a vyšších.


## <a name="in-this-section"></a>V této části
[Vzájemná izolace částí aplikace pomocí zástupných procedur za účelem testování jednotek](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

[Izolace aplikace od jiných sestavení pomocí testů shim za účelem testování jednotek](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

[Vytváření, kompilace a konvence pojmenování kódu v Napodobeniny Microsoft](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
