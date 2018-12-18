---
title: Pomocí zástupných procedury k izolování částí aplikace pro testování částí od sebe navzájem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73519dd9-f3d5-49b6-a634-38881b459ea4
caps.latest.revision: 19
ms.author: gewarren
manager: douge
ms.openlocfilehash: cc12f77a8f1c3443606537dd6f818e9ee6625327
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853179"
---
# <a name="using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing"></a>Vzájemná izolace částí aplikace pomocí zástupných procedury za účelem testování částí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typy zástupných procedur * jsou jedním ze dvou technologií, které rozhraní Microsoft Fakes poskytuje, abyste mohli snadno izolovat komponenty, které testujete od ostatních součástí, které volá. Zástupná procedura představuje malou část kódu, která během testování zaujímá místo jiné součásti. Výhodou použití zástupné procedury je to, že vrací konzistentní výsledky, čímž usnadňuje psaní testu. A testy můžete spustit i v případě, že ostatní součásti ještě nefungují.  
  
 A přehled o stručnou příručku k rozhraní Fakes, najdete v části [izolace kódu v rámci testu s Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
 Chcete-li použít zástupné procedury, musíte napsat součást tak, aby pro odkazování na ostatní části aplikace používala pouze rozhraní, a nikoliv třídy. To je dobrý postup při návrhu, protože je méně pravděpodobné, že změny v jedné části budou vyžadovat provedení změn i v jiné části. Při testování to umožňuje nahradit zástupnou proceduru reálnou součástí.  
  
 Chceme otestovat součást StockAnalyzer uvedenou na obrázku. Obvykle používá další součást RealStockFeed. Ale součást RealStockFeed vrací při každém volání svých metod jiné výsledky, což znesnadňuje testování součásti StockAnalyzer.  Během testování ji nahradíme jinou třídou, StubStockFeed.  
  
 ![Real a zástupné třídy odpovídat jedno rozhraní. ](../test/media/fakesinterfaces.png "FakesInterfaces")  
  
 Vzhledem k tomu, že zástupné procedury závisí na vaší schopnosti strukturovat váš kód tímto způsobem, můžete použít zástupné procedury k izolování jedné části vaší aplikace od jiné. Chcete-li ji izolovat od ostatních sestavení, která nejsou pod vaší kontrolou, jako je například sestavení System.dll, obvykle zřejmě použijete překrytí. Zobrazit [izolace aplikace od ostatních sestavení pro testování částí pomocí Překryvné ovladače](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).  
  
 **Požadavky**  
  
-   Visual Studio Enterprise  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   [Jak používat zástupné procedury](#how)  
  
    -   [Návrh pro vkládání závislostí](#Dependency)  
  
    -   [Generování zástupných procedur](#GeneratingStubs)  
  
    -   [Psaní testu se zástupnými procedurami](#WriteTest)  
  
    -   [Ověření hodnot parametrů](#mocks)  
  
-   [Zástupné procedury pro různé druhy členů typu](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md#BKMK_Stub_basics)  
  
    -   [Metody](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md#BKMK_Methods)  
  
    -   [Vlastnosti](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md#BKMK_Properties)  
  
    -   [Události](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md#BKMK_Events)  
  
    -   [Obecné metody](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md#BKMK_Generic_methods)  
  
    -   [Zástupné procedury virtuálních tříd](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md#BKMK_Partial_stubs)  
  
-   [Ladění zástupných procedur](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md#BKMK_Debugging_stubs)  
  
-   [Omezení zástupných procedur](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md#BKMK_Stub_limitation)  
  
-   [Změna výchozího chování zástupných procedur](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md#BKMK_Changing_the_default_behavior_of_stubs)  
  
##  <a name="How"></a> Jak používat zástupné procedury  
  
###  <a name="Dependency"></a> Návrh pro vkládání závislostí  
 Abyste mohli používat zástupné procedury, musí být vaše aplikace navržena tak, aby různé součásti nebyly závislé navzájem, ale byly závislé pouze na definicích rozhraní. Místo toho, aby byly součásti vázány v době kompilace, jsou propojeny v době běhu. Tento způsob napomáhá vytvářet software, který je robustní a snadno aktualizovatelný, protože změny nejsou obvykle přenášeny přes hranice součástí. Doporučujeme jej dodržovat, i pokud nepoužíváte zástupné procedury. Pokud píšete nový kód, je snadné sledovat [injektáž závislostí](http://en.wikipedia.org/wiki/Dependency_injection) vzor. Při psaní testů pro stávající software jej můžete chtít refaktorovat. V případě, že by to bylo nepraktické, můžete místo toho zvážit použití překrytí.  
  
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
  
- Kód jakékoli součásti aplikace by nikdy neměl explicitně odkazovat na třídu v jiné součásti, deklarace nebo v `new` příkazu. Místo toho by měly být proměnné a parametry deklarovány pomocí rozhraní. Instance součástí by měly by vytvořeny pouze kontejnerem součásti.  
  
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
  
###  <a name="GeneratingStubs"></a> Generování zástupných procedur  
 Oddělili jste třídu, kterou chcete testovat, od ostatních součástí, které používá. Oddělení umožňuje vytvořit robustnější a flexibilnější aplikaci a také propojit testovanou součást s implementacemi zástupných procedur rozhraní pro testovací účely.  
  
 Můžete jednoduše zapsat zástupné procedury jako třídy obvyklým způsobem. Ale rozhraní Microsoft Fakes vám nabízí dynamičtější způsob vytváření nejvhodnější zástupné procedury pro každý test.  
  
 Chcete-li použít zástupné procedury, musíte nejdříve vygenerovat typy zástupných procedur z definic rozhraní.  
  
##### <a name="adding-a-fakes-assembly"></a>Přidání napodobeniny sestavení  
  
1.  V Průzkumníku řešení rozbalte uzel projektu jednotkového testu **odkazy**.  
  
    -   Pokud pracujete v jazyce Visual Basic, musíte vybrat **zobrazit všechny soubory** v panelu nástrojů Průzkumníka řešení, chcete-li zobrazit seznam odkazů.  
  
2.  Vyberte sestavení, které obsahuje definice rozhraní, pro které chcete vytvořit zástupné procedury.  
  
3.  V místní nabídce zvolte **přidat napodobeniny sestavení**.  
  
###  <a name="WriteTest"></a> Psaní testu se zástupnými procedurami  
  
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
  
 Zvláštní část kouzla tady je třída `StubIStockFeed`. Pro každý veřejný typ v odkazovaném sestavení generuje mechanismus rozhraní Microsoft Fakes zástupnou třídu. Název zástupné třídy je odvozený od názvu rozhraní s "`Fakes.Stub`" jako předponu a připojenými parametry názvů typu.  
  
 Zástupné procedury jsou také generovány pro mechanismy získání a nastavení vlastností, pro události a pro obecné metody.  
  
###  <a name="mocks"></a> Ověření hodnot parametrů  
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
  
##  <a name="BKMK_Stub_basics"></a> Zástupné procedury pro různé druhy členů typu  
  
###  <a name="BKMK_Methods"></a> Metody  
 Jak je popsáno v příkladu, mohou být metody zastoupeny připojením delegáta k instanci zástupné třídy. Název typu zástupné procedury je odvozen z názvu metody a parametrů. Mějme například následující `IMyInterface` rozhraní a metoda `MyMethod`:  
  
```csharp  
// application under test  
interface IMyInterface   
{  
    int MyMethod(string value);  
}  
```  
  
 Připojíme zástupnou proceduru k `MyMethod` , která vždy vrátí 1:  
  
```csharp  
// unit test code  
  var stub = new StubIMyInterface ();  
  stub.MyMethodString = (value) => 1;  
  
```  
  
 Pokud neposkytnete zástupnou proceduru pro funkci, vygeneruje rozhraní Fakes funkci, která vrátí výchozí hodnotu návratového typu. Pro čísla, výchozí hodnota je 0, a pro typy tříd je `null` (C#) nebo `Nothing` (Visual Basic).  
  
###  <a name="BKMK_Properties"></a> Vlastnosti  
 Funkce pro nastavení a získání vlastnosti jsou vystaveny jako samostatní delegáti a mohou být samostatně zastoupeny. Představme si třeba, `Value` vlastnost `IMyInterface`:  
  
```csharp  
// code under test  
interface IMyInterface   
{  
    int Value { get; set; }  
}  
  
```  
  
 Doporučujeme připojit delegáty k metody getter a setter `Value` pro simulaci automatické vlastnosti:  
  
```csharp  
// unit test code  
int i = 5;  
var stub = new StubIMyInterface();  
stub.ValueGet = () => i;  
stub.ValueSet = (value) => i = value;  
  
```  
  
 Pokud neposkytnete metody zástupných procedur pro funkci nastavení nebo získání vlastnosti, vygeneruje rozhraní Fakes zástupnou proceduru, která ukládá hodnoty, takže zástupná vlastnost funguje jako jednoduchá proměnná.  
  
###  <a name="BKMK_Events"></a> Události  
 Události jsou vystaveny jako pole delegáta. Výsledkem je, že jakoukoli zastoupenou událost lze jednoduše aktivovat vyvoláním pole zálohování události. Zvažte následující rozhraní pro zastoupení:  
  
```csharp  
// code under test  
interface IWithEvents   
{  
    event EventHandler Changed;  
}  
```  
  
 Aby se vyvolala `Changed` událost, jednoduše vyvolat delegáta zálohování:  
  
```csharp  
// unit test code  
  var withEvents = new StubIWithEvents();  
  // raising Changed  
  withEvents.ChangedEvent(withEvents, EventArgs.Empty);  
  
```  
  
###  <a name="BKMK_Generic_methods"></a> Obecné metody  
 Poskytnutím delegáta pro každou požadovanou instanci metody je možné zastoupit obecné metody. Mějme například následující rozhraní obsahující obecnou metodu:  
  
```csharp  
// code under test  
interface IGenericMethod   
{  
    T GetValue<T>();  
}  
```  
  
 Lze napsat test, který zastupuje `GetValue<int>` instanciace:  
  
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
  
 Pokud kód volat `GetValue<T>` s kteroukoli další instancí, by zástupná procedura jednoduše volala chování.  
  
###  <a name="BKMK_Partial_stubs"></a> Zástupné procedury virtuálních tříd  
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
  
 Pokud nezadáte delegáta pro virtuální metodu, může rozhraní Fakes zadat buď výchozí chování, nebo může volat metodu v základní třídě. Chcete-li volat základní metodu, nastavte `CallBase` vlastnost:  
  
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
  
##  <a name="BKMK_Debugging_stubs"></a> Ladění zástupných procedur  
 Typy zástupných procedur jsou navrženy pro zajištění plynulého ladění. Standardně má ladicí program pokyn, aby přešel přes jakýkoli generovaný kód. Měl by tedy vstoupit přímo do vlastních implementací člena, které byly připojeny k zástupné proceduře.  
  
##  <a name="BKMK_Stub_limitation"></a> Omezení zástupných procedur  
  
1.  Signatury metody s ukazateli nejsou podporovány.  
  
2.  Zapečetěné třídy nebo statické metody nemohou být zastoupeny, protože jsou typy zástupných procedur závislé na odbavení virtuální metody. Pro tyto případy použijte typy překrytí, jak je popsáno v [izolace aplikace od ostatních sestavení pro testování částí pomocí Překryvné ovladače](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)  
  
##  <a name="BKMK_Changing_the_default_behavior_of_stubs"></a> Změna výchozího chování zástupných procedur  
 Každý generovaný typ zástupné procedury obsahuje instanci `IStubBehavior` rozhraní (až `IStub.InstanceBehavior` vlastnost). Chování je voláno pokaždé, když klient volá člen bez připojeného vlastního delegáta. Pokud chování nebylo nastaveno, bude používat instanci vrácenou `StubsBehaviors.Current` vlastnost. Ve výchozím nastavení, vrátí tato vlastnost chování, které se vyvolá `NotImplementedException` výjimky.  
  
 Chování můžete kdykoli změnit tak, že nastavíte `InstanceBehavior` vlastnost na jakékoli zástupné instanci. Například následující fragment kódu změní chování, které nic nedělá nebo vrací výchozí hodnotu návratového typu: `default(T)`:  
  
```csharp  
// unit test code  
var stub = new StubIFileSystem();  
// return default(T) or do nothing  
stub.InstanceBehavior = StubsBehaviors.DefaultValue;  
```  
  
 Chování lze také změnit globálně pro všechny zástupné objekty, pro které nebyla chování nastaveno nastavením `StubsBehaviors.Current` vlastnost:  
  
```csharp  
// unit test code  
//change default behavior for all stub instances  
//where the behavior has not been set  
StubBehaviors.Current =   
    BehavedBehaviors.DefaultValue;  
```  
  
## <a name="external-resources"></a>Externí zdroje  
  
### <a name="guidance"></a>Doprovodné materiály  
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 2: testování částí: testování uvnitř](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Viz také  
 [Izolace testovaného kódu pomocí zástupného rozhraní Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)



