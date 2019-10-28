---
title: Izolace aplikace při testování částí pomocí překrytí
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
author: jillre
dev_langs:
- CSharp
- VB
ms.openlocfilehash: e4a59cb4e3372e16634cddde2a163ac94ca73d24
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982801"
---
# <a name="use-shims-to-isolate-your-app-for-unit-testing"></a>Izolace vaší aplikace při testování částí pomocí překrytí

**Typy překrytí** představují jednu ze dvou technologií, které Microsoft předstírá Framework používá k izolaci testovaných komponent z prostředí. Překrytí volání specifických metod do kódu, který píšete jako součást testu. Mnoho metod vrací různé výsledky závislé na vnějších podmínkách, ale překrytí je pod kontrolou testu a může vracet konzistentní výsledky při každém volání. To usnadňuje zápis testů.

Použijte *překrytí* k izolaci kódu ze sestavení, která nejsou součástí vašeho řešení. Chcete-li izolovat součásti vašeho řešení od sebe navzájem, použijte zástupné *procedury*.

Přehled a pokyny pro rychlé spuštění najdete v tématu věnovaném [izolaci testovaného kódu pomocí napodobenin společnosti Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md).

**Požadavky**

- Visual Studio Enterprise
- .NET Framework projekt

> [!NOTE]
> .NET Standard projekty nejsou podporovány.

## <a name="example-the-y2k-bug"></a>Příklad: Chyba Y2K

Vezměte v úvahu metodu, která vyvolá výjimku od 1. ledna 2000:

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Testování této metody je problematické, protože program závisí na `DateTime.Now`, metodě, která závisí na hodinách počítače, nedeterministické metodě závislé na prostředí. Kromě toho `DateTime.Now` je statická vlastnost, takže typ zástupné procedury se tady nedá použít. Tento problém je příznaky potíží s izolací při testování částí: programy, které přímo volají rozhraní API pro databáze, komunikují s webovými službami atd., mají těžko test jednotek, protože jejich logika závisí na prostředí.

Toto je místo, kde by se měly použít typy překrytí. Typy překrytí poskytují mechanismus pro vyhlídka libovolné metody .NET na uživatelsky definovaný delegát. Typy překrytí jsou kódy generované generátorem falešného kódu a používají delegáty, které volají typy překrytí pro určení nových implementací metody.

Následující test ukazuje, jak použít typ překrytí, `ShimDateTime`, k poskytnutí vlastní implementace DateTime. Now:

```csharp
//unit test code
// create a ShimsContext cleans up shims
using (ShimsContext.Create()) {
    // hook delegate to the shim method to redirect DateTime.Now
    // to return January 1st of 2000
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);
    Y2KChecker.Check();
}
```

## <a name="how-to-use-shims"></a>Jak používat překrytí

Nejprve přidejte napodobeniny sestavení:

1. V **Průzkumník řešení**rozbalte uzel **odkazy** projektu testování jednotek.

   - Pokud pracujete v Visual Basic, vyberte možnost **Zobrazit všechny soubory** na panelu nástrojů **Průzkumník řešení** , aby se zobrazil uzel **odkazy** .

2. Vyberte sestavení, které obsahuje definice třídy, pro které chcete vytvořit překrytí. Pokud například chcete překrýt **data a času**, vyberte **System. dll**.

3. V místní nabídce vyberte možnost **Přidat napodobeniny sestavení**.

### <a name="use-shimscontext"></a>Použití ShimsContext

Při použití typů překrytí v rozhraní testování částí zabalte testovací kód v `ShimsContext` pro kontrolu doby života překrytí. V opačném případě překrytí bude poslední, dokud se doména AppDomain vypne. Nejjednodušší způsob, jak vytvořit `ShimsContext`, je použití statické `Create()` metody, jak je znázorněno v následujícím kódu:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

Je velmi důležité, aby každý kontext překrytí správně odstranil. Jako pravidlo pro palec volejte `ShimsContext.Create` uvnitř příkazu `using`, aby se zajistilo správné mazání registrovaných překrytí. Například můžete zaregistrovat překrytí pro testovací metodu, která nahrazuje metodu `DateTime.Now` s delegátem, který vždy vrátí první z ledna 2000. Pokud zapomenete zrušit registraci registrovaného překrytí v testovací metodě, zbytek testovacího běhu vždy vrátí první z lednu 2000 jako hodnotu `DateTime.Now`. To může být překvapivé a matoucí.

### <a name="write-a-test-with-shims"></a>Zápis testu s překrytím

V testovacím kódu vložte pro metodu, kterou chcete naklonovat, *prohlídku* . Příklad:

```csharp
[TestClass]
public class TestClass1
{
        [TestMethod]
        public void TestCurrentYear()
        {
            int fixedYear = 2000;

            using (ShimsContext.Create())
            {
              // Arrange:
                // Detour DateTime.Now to return a fixed date:
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

Názvy tříd překrytí jsou vytvářeny pomocí předpony `Fakes.Shim` původnímu názvu typu.

Překrytí fungují tak, že se do testovaného testovaného testovaného testovaného testovaného programu vloží *detreke* . Bez ohledu na to, jestli dojde k volání původní metody, provede tento systém napodobeniny, aby se místo volání reálné metody volala kód překrytí.

Všimněte si, že se v době běhu vytváří a odstraňují dejezdy. Je nutné vždy vytvořit rozhlídku během životnosti `ShimsContext`. Když je uvolněn, všechna překrytí, která jste vytvořili v době, kdy byla aktivní, jsou odebrána. Nejlepším způsobem, jak to provést, je uvnitř příkazu `using`.

Může se zobrazit chyba sestavení informující o tom, že obor názvů napodobeniny neexistuje. Tato chyba se někdy zobrazuje, když dojde k dalším chybám při kompilaci. Opravte ostatní chyby a zmizí.

## <a name="shims-for-different-kinds-of-methods"></a>Překrytí pro různé druhy metod

Typy překrytí umožňují nahradit libovolnou metodu .NET, včetně statických metod nebo nevirtuálních metod, s vlastními delegáty.

### <a name="static-methods"></a>Statické metody

Vlastnosti pro připojení překrytí statickým metodám jsou umístěny v typu překrytí. Každá vlastnost má pouze metodu Setter, která může být použita pro připojení delegáta k cílové metodě. Například vzhledem k třídě `MyClass` se statickou metodou `MyMethod`:

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

K `MyMethod` můžeme připojit doplňkový kód, který vždycky vrátí hodnotu 5:

```csharp
// unit test code
ShimMyClass.MyMethod = () => 5;
```

### <a name="instance-methods-for-all-instances"></a>Metody instance (pro všechny instance)

Podobně jako statické metody mohou být metody instance překryté pro všechny instance. Vlastnosti pro připojení těchto překrytí jsou umístěny do vnořeného typu s názvem AllInstances, aby se předešlo nejasnostem. Například vzhledem k třídě `MyClass` s metodou instance `MyMethod`:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Můžete připojit překrytí pro `MyMethod`, které vždycky vrátí hodnotu 5 bez ohledu na instanci:

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

Struktura generovaného typu ShimMyClass vypadá jako následující kód:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public static class AllInstances {
        public static Func<MyClass, int>MyMethod {
            set {
                ...
            }
        }
    }
}
```

Všimněte si, že falešné objekty předá instanci runtime jako první argument delegáta v tomto případě.

### <a name="instance-methods-for-one-runtime-instance"></a>Metody instance (pro jednu instanci modulu runtime)

Metody instance mohou být také překryté různými delegáty na základě přijímače volání. To umožňuje, aby stejná metoda instance měla různé chování pro jednotlivé instance typu. Vlastnosti pro nastavení těchto překrytí jsou metody instancí samotného typu překrytí. Každý typ překrytí instancemi je také přidružen k nezpracované instanci typu překryté.

Například vzhledem k třídě `MyClass` s metodou instance `MyMethod`:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Můžeme nastavit dva typy překrytí MyMethod tak, že první z nich vždy vrátí hodnotu 5 a druhá vždycky vrátí hodnotu 10:

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

Struktura generovaného typu ShimMyClass vypadá jako následující kód:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public Func<int> MyMethod {
        set {
            ...
        }
    }
    public MyClass Instance {
        get {
            ...
        }
    }
}
```

Ke skutečné instanci typu překryté lze přistupovat prostřednictvím vlastnosti instance:

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

Typ překrytí má také implicitní převod na typ překryté, takže můžete obvykle jednoduše použít typ překrytí, jak je:

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime instance
```

### <a name="constructors"></a>Konstruktory

Konstruktory mohou být také překryté, aby bylo možné připojit typy překrytí k budoucím objektům. Každý konstruktor je zveřejněn jako konstruktor statické metody v typu překrytí. Například pro třídu `MyClass` s konstruktorem, který přebírá celé číslo:

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Nastavíme typ překrytí konstruktoru tak, aby každá budoucí instance vrátila hodnotu-5 při vyvolání hodnoty getter bez ohledu na hodnotu v konstruktoru:

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

Každý typ překrytí zpřístupňuje dva konstruktory. Výchozí konstruktor by měl být použit, pokud je potřeba nová instance, zatímco konstruktor, který přebírá instanci překryté jako argument, by měl být použit pouze v překrytí konstruktoru:

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

Struktura generovaného typu ShimMyClass se podobá následujícímu kódu:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass>
{
    public static Action<MyClass, int> ConstructorInt32 {
        set {
            ...
        }
    }

    public ShimMyClass() { }
    public ShimMyClass(MyClass instance) : base(instance) { }
    ...
}
```

### <a name="base-members"></a>Základní členové

K vlastnostem překrytí základních členů lze přivodit vytvořením překrytí pro základní typ a předáním podřízené instance jako parametru konstruktoru základní třídy Shim.

Například pro třídu `MyBase` s metodou instance `MyMethod` a podtype `MyChild`:

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

Můžete nastavit překrytí `MyBase` vytvořením nového překrytí `ShimMyBase`:

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

Všimněte si, že podřízený typ překrytí je implicitně převeden na podřízenou instanci, pokud je předán jako parametr do základního konstruktoru překrytí.

Struktura generovaného typu ShimMyChild a ShimMyBase se podobá následujícímu kódu:

```csharp
// Fakes generated code
public class ShimMyChild : ShimBase<MyChild> {
    public ShimMyChild() { }
    public ShimMyChild(Child child)
        : base(child) { }
}
public class ShimMyBase : ShimBase<MyBase> {
    public ShimMyBase(Base target) { }
    public Func<int> MyMethod
    { set { ... } }
}
```

### <a name="static-constructors"></a>Statické konstruktory

Typy překrytí zpřístupňují statickou metodu `StaticConstructor` pro překrytí statického konstruktoru typu. Vzhledem k tomu, že statické konstruktory jsou prováděny pouze jednou, je nutné zajistit, aby překrytí bylo nakonfigurováno před tím, než bude k dispozici libovolný člen typu.

### <a name="finalizers"></a>Finalizační metody

Finalizační metody nejsou v napodobeninách podporovány.

### <a name="private-methods"></a>Soukromé metody

Generátor falešného kódu vytvoří vlastnosti překrytí pro privátní metody, které mají pouze viditelné typy v signatuře, to znamená, že typy parametrů a návratový typ jsou viditelné.

### <a name="binding-interfaces"></a>Rozhraní vazby

Když typ překryté implementuje rozhraní, generátor kódu vygeneruje metodu, která umožňuje vytvořit vazby všech členů z tohoto rozhraní najednou.

Například s ohledem na třídu `MyClass`, která implementuje `IEnumerable<int>`:

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}
```

Implementací metody bind můžete překrýt implementace `IEnumerable<int>` v MyClass.

```csharp
// unit test code
var shimMyClass = new ShimMyClass();
shimMyClass.Bind(new List<int> { 1, 2, 3 });
```

Struktura generovaného typu ShimMyClass se podobá následujícímu kódu:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public ShimMyClass Bind(IEnumerable<int> target) {
        ...
    }
}
```

## <a name="change-the-default-behavior"></a>Změna výchozího chování

Každý generovaný typ překrytí uchovává instanci `IShimBehavior` rozhraní prostřednictvím vlastnosti `ShimBase<T>.InstanceBehavior`. Chování se používá vždy, když klient volá člen instance, který nebyl explicitně překryté.

Pokud chování nebylo explicitně nastaveno, použije instanci vrácenou vlastností static `ShimsBehaviors.Current`. Ve výchozím nastavení tato vlastnost vrací chování, které vyvolá výjimku `NotImplementedException`.

Toto chování lze kdykoli změnit nastavením vlastnosti `InstanceBehavior` v jakékoli instanci překrytí. Například následující fragment kódu změní překrytí na chování, které nedělá nic nebo vrátí výchozí hodnotu návratového typu – to znamená `default(T)`:

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;
```

Chování je také možné globálně změnit pro všechny instance překryté, pro které nebyla explicitně nastavena vlastnost `InstanceBehavior` nastavením vlastnosti static `ShimsBehaviors.Current`:

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimsBehaviors.Current = ShimsBehaviors.DefaultValue;
```

## <a name="detect-environment-accesses"></a>Detekovat přístup k prostředí

Je možné připojit chování ke všem členům, včetně statických metod určitého typu, přiřazením chování `ShimsBehaviors.NotImplemented` statické vlastnosti `Behavior` odpovídajícího typu překrytí:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

## <a name="concurrency"></a>Souběžnost

Typy překrytí se vztahují na všechna vlákna v doméně AppDomain a nemají spřažení vláken. Toto je důležitý fakt, pokud plánujete použít Test Runner, který podporuje souběžnost. Testy zahrnující typy překrytí nemůžou běžet souběžně. Tato vlastnost není vynutila modulem runtime napodobeniny.

## <a name="call-the-original-method-from-the-shim-method"></a>Volání původní metody z metody Shim

Představte si, že chcete po ověření názvu souboru předaného do metody napsat text do systému souborů. V takovém případě byste měli zavolat původní metodu uprostřed metody Shim.

Prvním přístupem k vyřešení tohoto problému je zabalení volání původní metody pomocí delegáta a `ShimsContext.ExecuteWithoutShims()`, jako v následujícím kódu:

```csharp
// unit test code
ShimFile.WriteAllTextStringString = (fileName, content) => {
  ShimsContext.ExecuteWithoutShims(() => {

      Console.WriteLine("enter");
      File.WriteAllText(fileName, content);
      Console.WriteLine("leave");
  });
};
```

Dalším přístupem je nastavení překrytí na hodnotu null, volání původní metody a obnovení překrytí.

```csharp
// unit test code
ShimsDelegates.Action<string, string> shim = null;
shim = (fileName, content) => {
  try {
    Console.WriteLine("enter");
    // remove shim in order to call original method
    ShimFile.WriteAllTextStringString = null;
    File.WriteAllText(fileName, content);
  }
  finally
  {
    // restore shim
    ShimFile.WriteAllTextStringString = shim;
    Console.WriteLine("leave");
  }
};
// initialize the shim
ShimFile.WriteAllTextStringString = shim;
```

## <a name="systemenvironment"></a>System. Environment

Pro překrytí <xref:System.Environment?displayProperty=fullName> přidejte následující obsah do souboru mscorlib. napodobeniny po elementu **sestavení** :

```xml
<ShimGeneration>
    <Add FullName="System.Environment"/>
</ShimGeneration>
```

Po opětovném sestavení řešení jsou metody a vlastnosti ve třídě <xref:System.Environment?displayProperty=fullName> k dispozici pro překryté, například:

```csharp
System.Fakes.ShimEnvironment.GetCommandLineArgsGet = ...
```

## <a name="limitations"></a>Omezení

Překrytí nelze použít pro všechny typy z knihovny tříd **mscorlib** a **System**třídy .NET Base.

## <a name="see-also"></a>Viz také:

- [Izolace testovaného kódu pomocí napodobenin společnosti Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Blog Petra Provost: překrytí sady Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Video (1h16): testování netestovaných kódů s napodobeninami v aplikaci Visual Studio 2012](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
