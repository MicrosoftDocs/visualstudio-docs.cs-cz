---
title: Použití zástupných procedur k izolaci částí aplikace od sebe navzájem při testování jednotek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 73519dd9-f3d5-49b6-a634-38881b459ea4
caps.latest.revision: 19
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a230b55149152ba1d195f487951323eda855b8b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657143"
---
# <a name="using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing"></a>Vzájemná izolace částí aplikace pomocí zástupných procedury za účelem testování částí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typy zástupných procedur * jsou jedna ze dvou technologií, které Microsoft předstírá rozhraní představuje, aby vám umožnila snadno izolovat komponentu, kterou testujete, z jiných komponent, které volá. Zástupná procedura představuje malou část kódu, která během testování zaujímá místo jiné součásti. Výhodou použití zástupné procedury je to, že vrací konzistentní výsledky, čímž usnadňuje psaní testu. A testy můžete spustit i v případě, že ostatní součásti ještě nefungují.

 Přehled a Úvodní příručku k napodobeninám naleznete v části [izolování testovaného kódu pomocí napodobenin společnosti Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md).

 Chcete-li použít zástupné procedury, musíte napsat součást tak, aby pro odkazování na ostatní části aplikace používala pouze rozhraní, a nikoliv třídy. To je dobrý postup při návrhu, protože je méně pravděpodobné, že změny v jedné části budou vyžadovat provedení změn i v jiné části. Při testování to umožňuje nahradit zástupnou proceduru reálnou součástí.

 Chceme otestovat součást StockAnalyzer uvedenou na obrázku. Obvykle používá další součást RealStockFeed. Ale součást RealStockFeed vrací při každém volání svých metod jiné výsledky, což znesnadňuje testování součásti StockAnalyzer.  Během testování ji nahradíme jinou třídou, StubStockFeed.

 ![Třídy Real a stub jsou v souladu s jedním rozhraním.](../test/media/fakesinterfaces.png "FakesInterfaces")

 Vzhledem k tomu, že zástupné procedury závisí na vaší schopnosti strukturovat váš kód tímto způsobem, můžete použít zástupné procedury k izolování jedné části vaší aplikace od jiné. Chcete-li ji izolovat od ostatních sestavení, která nejsou pod vaší kontrolou, jako je například sestavení System.dll, obvykle zřejmě použijete překrytí. Viz [použití překrytí k izolaci aplikace od jiných sestavení pro testování částí](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

 **Požadavky**

- Visual Studio Enterprise

## <a name="How"></a>Jak používat zástupné procedury

### <a name="Dependency"></a>Návrh pro vkládání závislostí
 Abyste mohli používat zástupné procedury, musí být vaše aplikace navržena tak, aby různé součásti nebyly závislé navzájem, ale byly závislé pouze na definicích rozhraní. Místo toho, aby byly součásti vázány v době kompilace, jsou propojeny v době běhu. Tento způsob napomáhá vytvářet software, který je robustní a snadno aktualizovatelný, protože změny nejsou obvykle přenášeny přes hranice součástí. Doporučujeme jej dodržovat, i pokud nepoužíváte zástupné procedury. Pokud píšete nový kód, je snadné postupovat podle vzoru [vkládání závislostí](http://en.wikipedia.org/wiki/Dependency_injection) . Při psaní testů pro stávající software jej můžete chtít refaktorovat. V případě, že by to bylo nepraktické, můžete místo toho zvážit použití překrytí.

 Začněme tuto diskusi motivačním příkladem, který je uveden na obrázku. Třída StockAnalyzer čte ceny akcií a vytváří některé zajímavé výsledky. Má některé veřejné metody, které chceme otestovat. Abychom si to nekomplikovali, podívejme se na jednu z těchto metod, která je velmi jednoduchá a vytváří sestavy s aktuální cenou určité akcie. Chceme napsat jednotkový test této metody. Zde je první návrh testu:

```csharp
[TestMethod]
public void TestMethod1()
{
    // Arrange:
    var analyzer = new StockAnalyzer();
    // Act:
    var result = analyzer.GetContosoPrice();
    // Assert:
    Assert.AreEqual(123, result); // Why 123?
}
```

```vb
<TestMethod()> Public Sub TestMethod1()
    ' Arrange:
    Dim analyzer = New StockAnalyzer()
    ' Act:
    Dim result = analyzer.GetContosoPrice()
    ' Assert:
    Assert.AreEqual(123, result) ' Why 123?
End Sub
```

 Jeden problém s tímto testem je okamžitě zřejmý: ceny akcií se liší a výraz tudíž obvykle selže.

 Dalším problémem může být, že součást StockFeed, která je použita součástí StockAnalyzer, je stále ve vývoji. Zde je první návrh kódu testované metody:

```csharp
public int GetContosoPrice()
{
    var stockFeed = new StockFeed(); // NOT RECOMMENDED
    return stockFeed.GetSharePrice("COOO");
}
```

```vb
Public Function GetContosoPrice()
    Dim stockFeed = New StockFeed() ' NOT RECOMMENDED
    Return stockFeed.GetSharePrice("COOO")
End Function
```

 Ve stávající podobě se nemusí tato metoda kompilovat nebo může vyvolat výjimku, protože práce na třídě StockFeed není ještě dokončena.

 Vložení rozhraní řeší oba tyto problémy.

 Vložení rozhraní používá následující pravidlo:

- Kód jakékoli komponenty aplikace by nikdy neměl explicitně odkazovat na třídu v jiné komponentě, a to buď v deklaraci, nebo v příkazu `new`. Místo toho by měly být proměnné a parametry deklarovány pomocí rozhraní. Instance součástí by měly by vytvořeny pouze kontejnerem součásti.

   „Součást“ v tomto případě představuje třídu nebo skupinu tříd, které společně vyvíjíte a aktualizujete. Součást obvykle představuje kód v jednom projektu sady Visual Studio. Není příliš důležité oddělit třídy v rámci jedné součásti, protože jsou aktualizovány ve stejnou dobu.

   Rovněž není až tak důležité oddělit součásti od tříd s poměrně stabilní platformou, jako je například System.dll. Vytvoření rozhraní pro všechny tyto třídy by zbytečně zatěžovalo váš kód.

  Kód StockAnalyzer lze proto zlepšit oddělením od součásti StockFeed pomocí rozhraní, jako je například toto:

```csharp
public interface IStockFeed
{
    int GetSharePrice(string company);
}

public class StockAnalyzer
{
    private IStockFeed stockFeed;
    public Analyzer(IStockFeed feed)
    {
        stockFeed = feed;
    }
    public int GetContosoPrice()
    {
        return stockFeed.GetSharePrice("COOO");
    }
}
```

```vb
Public Interface IStockFeed
    Function GetSharePrice(company As String) As Integer
End Interface

Public Class StockAnalyzer
    ' StockAnalyzer can be connected to any IStockFeed:
    Private stockFeed As IStockFeed
    Public Sub New(feed As IStockFeed)
        stockFeed = feed
    End Sub
    Public Function GetContosoPrice()
        Return stockFeed.GetSharePrice("COOO")
    End Function
End Class

```

 V tomto příkladu je součásti StockAnalyzer předána implementace součásti IStockFeed, jakmile je vytvořena. U dokončené aplikace by inicializační kód provedl připojení:

```
analyzer = new StockAnalyzer(new StockFeed())
```

 Existují flexibilnější způsoby provedení tohoto připojení. Součást StockAnalyzer by například mohla přijmout objekt factory, který může vytvořit instanci různými implementacemi součásti IStockFeed v různých podmínkách.

### <a name="GeneratingStubs"></a>Generovat zástupné procedury
 Oddělili jste třídu, kterou chcete testovat, od ostatních součástí, které používá. Oddělení umožňuje vytvořit robustnější a flexibilnější aplikaci a také propojit testovanou součást s implementacemi zástupných procedur rozhraní pro testovací účely.

 Můžete jednoduše zapsat zástupné procedury jako třídy obvyklým způsobem. Ale rozhraní Microsoft Fakes vám nabízí dynamičtější způsob vytváření nejvhodnější zástupné procedury pro každý test.

 Chcete-li použít zástupné procedury, musíte nejdříve vygenerovat typy zástupných procedur z definic rozhraní.

##### <a name="adding-a-fakes-assembly"></a>Přidání napodobeniny sestavení

1. V Průzkumník řešení rozbalte **odkazy**projektu testování částí.

    - Pokud pracujete v Visual Basic, musíte vybrat **Zobrazit všechny soubory** na panelu nástrojů Průzkumník řešení, aby se zobrazil seznam odkazů.

2. Vyberte sestavení, které obsahuje definice rozhraní, pro které chcete vytvořit zástupné procedury.

3. V místní nabídce vyberte možnost **Přidat napodobeniny sestavení**.

### <a name="WriteTest"></a>Napište svůj test pomocí zástupných procedur

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

 Speciální část Magic je `StubIStockFeed` třídy. Pro každý veřejný typ v odkazovaném sestavení generuje mechanismus rozhraní Microsoft Fakes zástupnou třídu. Název třídy zástupné procedury je odvozen z názvu rozhraní, s "`Fakes.Stub`" jako předponu a s připojenými názvy typů parametrů.

 Zástupné procedury jsou také generovány pro mechanismy získání a nastavení vlastností, pro události a pro obecné metody.

### <a name="mocks"></a>Ověřují se hodnoty parametrů
 Můžete ověřit, že pokud vaše součást volá jinou součást, jsou předány správné hodnoty. Výraz můžete přidat buď do zástupné procedury, nebo můžete hodnotu uložit a ověřit ji v hlavní části testu. Příklad:

```csharp
[TestClass]
class TestMyComponent
{

    [TestMethod]
    public void TestVariableContosoPrice()
    {
     // Arrange:
        int priceToReturn;
        string companyCodeUsed;
        var componentUnderTest = new StockAnalyzer(new StubIStockFeed()
            {
               GetSharePriceString = (company) =>
                  {
                     // Store the parameter value:
                     companyCodeUsed = company;
                     // Return the value prescribed by this test:
                     return priceToReturn;
                  };
            };
        // Set the value that will be returned by the stub:
        priceToReturn = 345;

     // Act:
        int actualResult = componentUnderTest.GetContosoPrice();

     // Assert:
        // Verify the correct result in the usual way:
        Assert.AreEqual(priceToReturn, actualResult);

        // Verify that the component made the correct call:
        Assert.AreEqual("COOO", companyCodeUsed);
    }
...}

```

```vb
<TestClass()> _
Class TestMyComponent
    <TestMethod()> _
    Public Sub TestVariableContosoPrice()
        ' Arrange:
        Dim priceToReturn As Integer
        Dim companyCodeUsed As String = ""
        Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed()
        With stockFeed
            ' Implement the interface's method:
            .GetSharePriceString = _
                Function(company)
                    ' Store the parameter value:
                    companyCodeUsed = company
                    ' Return a fixed result:
                    Return priceToReturn
                End Function
        End With
        ' Create an object to test:
        Dim componentUnderTest As New StockAnalyzer(stockFeed)
        ' Set the value that will be returned by the stub:
        priceToReturn = 345

        ' Act:
        Dim actualResult As Integer = componentUnderTest.GetContosoPrice()

        ' Assert:
        ' Verify the correct result in the usual way:
        Assert.AreEqual(priceToReturn, actualResult)
        ' Verify that the component made the correct call:
        Assert.AreEqual("COOO", companyCodeUsed)
    End Sub
...
End Class
```

## <a name="BKMK_Stub_basics"></a>Zástupné procedury pro různé druhy členů typu

### <a name="BKMK_Methods"></a>Způsobů
 Jak je popsáno v příkladu, mohou být metody zastoupeny připojením delegáta k instanci zástupné třídy. Název typu zástupné procedury je odvozen z názvu metody a parametrů. Například s ohledem na následující `IMyInterface` rozhraní a `MyMethod` metody:

```csharp
// application under test
interface IMyInterface
{
    int MyMethod(string value);
}
```

 K `MyMethod`, který vždycky vrátí hodnotu 1, připojíme zástupnou proceduru:

```csharp
// unit test code
  var stub = new StubIMyInterface ();
  stub.MyMethodString = (value) => 1;

```

 Pokud neposkytnete zástupnou proceduru pro funkci, vygeneruje rozhraní Fakes funkci, která vrátí výchozí hodnotu návratového typu. Pro čísla je výchozí hodnota 0 a pro typy tříd je to `null` (C#) nebo `Nothing` (Visual Basic).

### <a name="BKMK_Properties"></a>Vlastnosti
 Funkce pro nastavení a získání vlastnosti jsou vystaveny jako samostatní delegáti a mohou být samostatně zastoupeny. Zvažte například vlastnost `Value` `IMyInterface`:

```csharp
// code under test
interface IMyInterface
{
    int Value { get; set; }
}

```

 Připravujeme delegáty pro metodu getter a setter `Value` pro simulaci automatické vlastnosti:

```csharp
// unit test code
int i = 5;
var stub = new StubIMyInterface();
stub.ValueGet = () => i;
stub.ValueSet = (value) => i = value;

```

 Pokud neposkytnete metody zástupných procedur pro funkci nastavení nebo získání vlastnosti, vygeneruje rozhraní Fakes zástupnou proceduru, která ukládá hodnoty, takže zástupná vlastnost funguje jako jednoduchá proměnná.

### <a name="BKMK_Events"></a>Událost
 Události jsou vystaveny jako pole delegáta. Výsledkem je, že jakoukoli zastoupenou událost lze jednoduše aktivovat vyvoláním pole zálohování události. Zvažte následující rozhraní pro zastoupení:

```csharp
// code under test
interface IWithEvents
{
    event EventHandler Changed;
}
```

 Pokud chcete vyvolat událost `Changed`, jednoduše vyvolá delegovaného delegáta:

```csharp
// unit test code
  var withEvents = new StubIWithEvents();
  // raising Changed
  withEvents.ChangedEvent(withEvents, EventArgs.Empty);

```

### <a name="BKMK_Generic_methods"></a>Obecné metody
 Poskytnutím delegáta pro každou požadovanou instanci metody je možné zastoupit obecné metody. Mějme například následující rozhraní obsahující obecnou metodu:

```csharp
// code under test
interface IGenericMethod
{
    T GetValue<T>();
}
```

 můžete napsat test, který má zástupnou proceduru vytváření instancí `GetValue<int>`:

```csharp
// unit test code
[TestMethod]
public void TestGetValue()
{
    var stub = new StubIGenericMethod();
    stub.GetValueOf1<int>(() => 5);

    IGenericMethod target = stub;
    Assert.AreEqual(5, target.GetValue<int>());
}
```

 Pokud byl kód volán `GetValue<T>` s jakoukoliv jinou instancí, by zástupná procedura jednoduše volala chování.

### <a name="BKMK_Partial_stubs"></a>Zástupné procedury virtuálních tříd
 V předchozích příkladech byly zástupné procedury vytvořeny z rozhraní. Můžete také vygenerovat zástupné procedury z třídy, která má virtuální nebo abstraktní členy. Příklad:

```csharp
// Base class in application under test
    public abstract class MyClass
    {
        public abstract void DoAbstract(string x);
        public virtual int DoVirtual(int n)
        { return n + 42; }
        public int DoConcrete()
        { return 1; }
    }
```

 V zástupné proceduře vygenerované z této třídy můžete nastavit metody delegáta pro DoAbstract() a DoVirtual(), ale nikoliv pro DoConcrete().

```csharp
// unit test
  var stub = new Fakes.MyClass();
  stub.DoAbstractString = (x) => { Assert.IsTrue(x>0); };
  stub.DoVirtualInt32 = (n) => 10 ;

```

 Pokud nezadáte delegáta pro virtuální metodu, může rozhraní Fakes zadat buď výchozí chování, nebo může volat metodu v základní třídě. Chcete-li vyvolat základní metodu, nastavte vlastnost `CallBase`:

```csharp
// unit test code
var stub = new Fakes.MyClass();
stub.CallBase = false;
// No delegate set – default delegate:
Assert.AreEqual(0, stub.DoVirtual(1));

stub.CallBase = true;
//No delegate set - calls the base:
Assert.AreEqual(43,stub.DoVirtual(1));
```

## <a name="BKMK_Debugging_stubs"></a>Ladění zástupných procedur
 Typy zástupných procedur jsou navrženy pro zajištění plynulého ladění. Standardně má ladicí program pokyn, aby přešel přes jakýkoli generovaný kód. Měl by tedy vstoupit přímo do vlastních implementací člena, které byly připojeny k zástupné proceduře.

## <a name="BKMK_Stub_limitation"></a>Omezení zástupných procedur

1. Signatury metody s ukazateli nejsou podporovány.

2. Zapečetěné třídy nebo statické metody nemohou být zastoupeny, protože jsou typy zástupných procedur závislé na odbavení virtuální metody. V takových případech použijte typy překrytí, jak je popsáno v tématu [použití překrytí k izolaci aplikace od jiných sestavení pro testování částí](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) .

## <a name="BKMK_Changing_the_default_behavior_of_stubs"></a>Změna výchozího chování zástupných procedur
 Každý generovaný typ stub obsahuje instanci rozhraní `IStubBehavior` (prostřednictvím vlastnosti `IStub.InstanceBehavior`). Chování je voláno pokaždé, když klient volá člen bez připojeného vlastního delegáta. Pokud chování nebylo nastaveno, bude použita instance vrácená vlastností `StubsBehaviors.Current`. Ve výchozím nastavení tato vlastnost vrací chování, které vyvolá výjimku `NotImplementedException`.

 Chování lze kdykoli změnit nastavením vlastnosti `InstanceBehavior` u jakékoli instance zástupné procedury. Například následující fragment kódu změní chování, které nedělá nic nebo vrátí výchozí hodnotu návratového typu: `default(T)`:

```csharp
// unit test code
var stub = new StubIFileSystem();
// return default(T) or do nothing
stub.InstanceBehavior = StubsBehaviors.DefaultValue;
```

 Chování lze také globálně změnit pro všechny objekty se zástupnými procedurami, pro které nebylo nastaveno chování nastavením vlastnosti `StubsBehaviors.Current`:

```csharp
// unit test code
//change default behavior for all stub instances
//where the behavior has not been set
StubBehaviors.Current =
    BehavedBehaviors.DefaultValue;
```

## <a name="external-resources"></a>Externí zdroje

### <a name="guidance"></a>Doprovodné materiály
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 2: testování částí: testování uvnitř](http://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Viz také
 [Izolace testovaného kódu pomocí zástupného rozhraní Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)
