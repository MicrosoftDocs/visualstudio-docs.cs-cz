---
title: Izolace aplikace od ostatních sestavení pomocí překrytí za účelem testování částí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d2a34de2-6527-4c21-8b93-2f268ee894b7
caps.latest.revision: 14
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa9db3e67b1f5ba5e183f8df0c7b34372476fb08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851170"
---
# <a name="using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>Izolace aplikace od ostatních sestavení pomocí překrytí za účelem testů jednotek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typy překrytí * * představují jednu ze dvou technologií, které Microsoft předstírá Framework používá k umožnění snadné izolace testovaných komponent z prostředí. Překrytí volání specifických metod do kódu, který píšete jako součást testu. Mnoho metod vrací různé výsledky závislé na vnějších podmínkách, ale překrytí je pod kontrolou testu a může vracet konzistentní výsledky při každém volání. To umožní vašim testům mnohem snazší zápis.

 Použijte překrytí k izolaci kódu ze sestavení, která nejsou součástí vašeho řešení. Chcete-li izolovat součásti vašeho řešení od sebe navzájem, doporučujeme použít zástupné procedury.

 Přehled a rychlé úvodní pokyny najdete v tématu [izolování testovaného kódu s napodobeninami Microsoftu](../test/isolating-code-under-test-with-microsoft-fakes.md) .

 **Požadavky**

- Visual Studio Enterprise

  Viz [video (1h16): testování kódu bez testovatelné s napodobeninami v aplikaci Visual Studio 2012](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)

## <a name="example-the-y2k-bug"></a><a name="BKMK_Example__The_Y2K_bug"></a> Příklad: Chyba Y2K
 Pojďme vzít v úvahu metodu, která vyvolá výjimku od 1. ledna 2000:

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}

```

 Testování této metody je obzvláště problematické, protože program závisí na `DateTime.Now` metodě, která závisí na hodinách počítače, nedeterministické metodě závislé na prostředí. Kromě toho `DateTime.Now` je statická vlastnost, takže typ zástupné procedury se tady nedá použít. Tento problém je příznaky potíží s izolací při testování částí: programy, které přímo volají rozhraní API pro databáze, komunikují s webovými službami a tak dále, je obtížné testování částí, protože jejich logika závisí na prostředí.

 Toto je místo, kde by se měly použít typy překrytí. Typy překrytí poskytují mechanismus pro vyhlídku libovolné metody .NET k delegátovi definovanému uživatelem. Typy překrytí jsou kódy generované generátorem falešného kódu a používají delegáty, které volají typy překrytí pro určení nových implementací metody.

 Následující test ukazuje, jak použít typ překrytí, `ShimDateTime` k poskytnutí vlastní implementace DateTime. Now:

```csharp
//unit test code
// create a ShimsContext cleans up shims
using (ShimsContext.Create()
    // hook delegate to the shim method to redirect DateTime.Now
    // to return January 1st of 2000
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);
    Y2KChecker.Check();
}

```

## <a name="how-to-use-shims"></a><a name="BKMK_Fakes_requirements"></a> Jak používat překrytí

### <a name="add-fakes-assemblies"></a><a name="AddFakes"></a> Přidat napodobeniny sestavení

1. V Průzkumník řešení rozbalte **odkazy**projektu testování částí.

    - Pokud pracujete v Visual Basic, musíte vybrat **Zobrazit všechny soubory** na panelu nástrojů Průzkumník řešení, aby se zobrazil seznam odkazů.

2. Vyberte sestavení obsahující definice tříd, pro které chcete vytvořit překrytí. Pokud například chcete překrýt data a času, vyberte System.dll

3. V místní nabídce vyberte možnost **Přidat napodobeniny sestavení**.

### <a name="use-shimscontext"></a><a name="ShimsContext"></a> Použití ShimsContext
 Při použití typů překrytí v rozhraní testování částí je nutné zabalit testovací kód v a `ShimsContext` řídit dobu života překrytí. Pokud to nepotřebujeme, překrytí by mělo být poslední, dokud se doména AppDomain nevypne. Nejjednodušší způsob, jak vytvořit, `ShimsContext` je použít statickou `Create()` metodu, jak je znázorněno v následujícím kódu:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}

```

 Je velmi důležité, aby každý kontext překrytí správně odstranil. Jako pravidlo pro palec vždy zavolejte `ShimsContext.Create` uvnitř `using` příkazu, aby se zajistilo správné zrušení zapsaných překrytí. Například můžete zaregistrovat překrytí pro testovací metodu, která nahrazuje `DateTime.Now` metodu delegátem, který vždy vrátí první z ledna 2000. Pokud zapomenete zrušit registraci registrovaného překrytí v testovací metodě, zbytek testovacího běhu vždy vrátí první z lednu 2000 jako hodnotu DateTime. Now. To může být suprising a matoucí.

### <a name="write-a-test-with-shims"></a><a name="WriteShims"></a> Zápis testu s překrytím
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

 Názvy tříd překrytí jsou vytvářeny pomocí předpony `Fakes.Shim` na původní název typu.

 Překrytí fungují tak, že se do testovaného testovaného testovaného testovaného testovaného programu vloží *detreke* . Bez ohledu na to, jestli dojde k volání původní metody, provede tento systém napodobeniny, aby se místo volání reálné metody volala kód překrytí.

 Všimněte si, že se v době běhu vytváří a odstraňují dejezdy. Je nutné vždy vytvořit rozhlídku v rámci životního cyklu `ShimsContext` . Když je uvolněn, všechna překrytí, která jste vytvořili v době, kdy byla aktivní, jsou odebrána. Nejlepším způsobem, jak to provést, je uvnitř `using` příkazu.

 Může se zobrazit chyba sestavení informující o tom, že obor názvů napodobeniny neexistuje. Tato chyba se někdy zobrazuje, když dojde k dalším chybám při kompilaci. Opravte ostatní chyby a zmizí.

## <a name="shims-for-different-kinds-of-methods"></a><a name="BKMK_Shim_basics"></a> Překrytí pro různé druhy metod
 Typy překrytí umožňují nahradit libovolnou metodu .NET, včetně statických metod nebo nevirtuálních metod, s vlastními delegáty.

### <a name="static-methods"></a><a name="BKMK_Static_methods"></a> Statické metody
 Vlastnosti pro připojení překrytí statickým metodám jsou umístěny v typu překrytí. Každá vlastnost má pouze metodu Setter, která může být použita pro připojení delegáta k cílové metodě. Například pro danou třídu `MyClass` se statickou metodou `MyMethod` :

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

 Můžeme připojit překrytí `MyMethod` , které vždycky vrátí hodnotu 5:

```csharp
// unit test code
ShimMyClass.MyMethod = () =>5;
```

### <a name="instance-methods-for-all-instances"></a><a name="BKMK_Instance_methods__for_all_instances_"></a> Metody instance (pro všechny instance)
 Podobně jako statické metody mohou být metody instance překryté pro všechny instance. Vlastnosti pro připojení těchto překrytí jsou umístěny do vnořeného typu s názvem AllInstances, aby se předešlo nejasnostem. Například pro danou třídu `MyClass` s metodou instance `MyMethod` :

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

 Můžete připojit překrytí `MyMethod` , které vždy vrátí hodnotu 5 bez ohledu na instanci:

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

### <a name="instance-methods-for-one-runtime-instance"></a><a name="BKMK_Instance_methods__for_one_instance_"></a> Metody instance (pro jednu instanci modulu runtime)
 Metody instance mohou být také překryté různými delegáty na základě přijímače volání. To umožňuje, aby stejná metoda instance měla různé chování pro jednotlivé instance typu. Vlastnosti pro nastavení těchto překrytí jsou metody instancí samotného typu překrytí. Každý typ překrytí instancemi je také přidružen k nezpracované instanci typu překryté.

 Například pro danou třídu `MyClass` s metodou instance `MyMethod` :

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
MyClass instance = shim; // implicit cast retrieves the runtime
                         // instance
```

### <a name="constructors"></a><a name="BKMK_Constructors"></a> Konstruktory
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

 Všimněte si, že každý typ překrytí zveřejňuje dva konstruktory. Výchozí konstruktor by měl být použit, pokud je potřeba nová instance, zatímco konstruktor, který přebírá instanci překryté jako argument, by měl být použit pouze v překrytí konstruktoru:

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

 Struktura generovaného typu ShimMyClass se podobá kódu followoing:

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

### <a name="base-members"></a><a name="BKMK_Base_members"></a> Základní členové
 K vlastnostem překrytí základních členů lze přivodit vytvořením překrytí pro základní typ a předáním podřízené instance jako parametru konstruktoru základní třídy Shim.

 Například pro danou třídu `MyBase` s metodou instance `MyMethod` a podtype `MyChild` :

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}

```

 Pro `MyBase` Vytvoření nového překrytí můžeme nastavit překrytí `ShimMyBase` :

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

### <a name="static-constructors"></a><a name="BKMK_Static_constructors"></a> Statické konstruktory
 Typy překrytí zpřístupňují statickou metodu `StaticConstructor` pro překrytí statického konstruktoru typu. Vzhledem k tomu, že statické konstruktory jsou prováděny pouze jednou, je nutné zajistit, aby bylo překrytí nakonfigurováno před jakýmkoli členem typu.

### <a name="finalizers"></a><a name="BKMK_Finalizers"></a> Finalizační metody
 Finalizační metody nejsou v napodobeninách podporovány.

### <a name="private-methods"></a><a name="BKMK_Private_methods"></a> Soukromé metody
 Generátor falešného kódu vytvoří vlastnosti překrytí pro privátní metody, které mají pouze viditelné typy v signatuře, tj. typy parametrů a návratový typ.

### <a name="binding-interfaces"></a><a name="BKMK_Binding_interfaces"></a> Rozhraní vazby
 Když typ překryté implementuje rozhraní, generátor kódu vygeneruje metodu, která umožňuje vytvořit vazby všech členů z tohoto rozhraní najednou.

 Například pro danou třídu `MyClass` , která implementuje `IEnumerable<int>` :

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}

```

 Implementací metody bind můžeme překrýt implementace `IEnumerable<int>` v metodě MyClass:

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

## <a name="changing-the-default-behavior"></a><a name="BKMK_Changing_the_default_behavior"></a> Změna výchozího chování
 Každý generovaný typ překrytí uchovává instanci `IShimBehavior` rozhraní prostřednictvím `ShimBase<T>.InstanceBehavior` Vlastnosti. Chování se používá vždy, když klient volá člen instance, který nebyl explicitně překryté.

 Pokud chování nebylo explicitně nastaveno, bude použita instance vrácená statickou `ShimsBehaviors.Current` vlastností. Ve výchozím nastavení tato vlastnost vrací chování, které vyvolá `NotImplementedException` výjimku.

 Toto chování lze kdykoli změnit nastavením `InstanceBehavior` vlastnosti u jakékoli instance překrytí. Například následující fragment kódu změní překrytí na chování, které nedělá nic nebo vrátí výchozí hodnotu návratového typu – to je výchozí (T):

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;

```

 Chování se dá také globálně změnit pro všechny instance překryté, pro které se `InstanceBehavior` vlastnost explicitně nenastavuje, nastavením `ShimsBehaviors.Current` vlastnosti static:

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimsBehaviors.Current =
    ShimsBehaviors.DefaultValue;

```

## <a name="detecting-environment-accesses"></a><a name="BKMK_Detecting_environment_accesses"></a> Zjišťování přístupů k prostředí
 Je možné připojit chování ke všem členům, včetně statických metod určitého typu, přiřazením `ShimsBehaviors.NotImplemented` chování statické vlastnosti `Behavior` odpovídajícího typu překrytí:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();

```

## <a name="concurrency"></a><a name="BKMK_Concurrency"></a> Concurrency
 Typy překrytí se vztahují na všechna vlákna v doméně AppDomain a nemají spřažení vláken. Toto je důležitý fakt, pokud plánujete použít testovací spouštěč, který podporuje souběžnost: testy zahrnující typy překrytí nemůžou běžet souběžně. Tuto vlastnost neenfored modulem runtime napodobeniny.

## <a name="calling-the-original-method-from-the-shim-method"></a><a name="BKMK_Calling_the_original_method_from_the_shim_method"></a> Volání původní metody z metody Shim
 Představte si, že po ověření názvu souboru předaného do metody jsme chtěli napsat text do systému souborů. V takovém případě chceme zavolat původní metodu uprostřed metody Shim.

 Prvním přístupem k vyřešení tohoto problému je zabalení volání původní metody pomocí delegáta a `ShimsContext.ExecuteWithoutShims()` jako v následujícím kódu:

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
    Console.WriteLine("enter”);
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

## <a name="limitations"></a><a name="BKMK_Limitations"></a> Určitá
 Překrytí nelze použít pro všechny typy z knihovny tříd **mscorlib** a **System**třídy .NET Base.

## <a name="external-resources"></a>Externí zdroje

### <a name="guidance"></a>Doprovodné materiály
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 2: testování částí: testování uvnitř](https://msdn.microsoft.com/library/jj159340.aspx)

## <a name="see-also"></a>Viz také
 [Izolace testovaného kódu s Microsoftem falešného](../test/isolating-code-under-test-with-microsoft-fakes.md) [blogu Petra Provost: Video překrytí sady Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2) [(1H16): testování testovatelné kódu s napodobeninami v aplikaci Visual Studio 2012](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
