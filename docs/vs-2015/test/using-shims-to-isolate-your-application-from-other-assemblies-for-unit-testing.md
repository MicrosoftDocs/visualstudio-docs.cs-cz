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
ms.openlocfilehash: 07e42c6b1e3e3537801c3d7420d2cad8dd119fa7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301422"
---
# <a name="using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>Izolace aplikace od ostatních sestavení pomocí překrytí za účelem testů jednotek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typy překrytí * * představují jednu ze dvou technologií, které Microsoft předstírá Framework používá k umožnění snadné izolace testovaných komponent z prostředí. Překrytí rozdělení volání konkrétní metody do kódu, který píšete v rámci testu. Mnoho metod vrátit různé výsledky závislé na externích podmínky, ale překrytí je pod kontrolou vašeho testu a může vrátit konzistentní výsledky při každém volání. Jednodušší testy k zápisu.

 Překryvné ovladače použijte k izolování váš kód ze sestavení, které nejsou součástí vašeho řešení. Součástí vašeho řešení od sebe navzájem izolovat, doporučujeme použít zástupné procedury.

 Přehled a rychlé úvodní pokyny najdete v tématu [izolování testovaného kódu s napodobeninami Microsoftu](../test/isolating-code-under-test-with-microsoft-fakes.md) .

 **Požadavky**

- Visual Studio Enterprise

  Viz [video (1h16): testování kódu bez testovatelné s napodobeninami v aplikaci Visual Studio 2012](https://go.microsoft.com/fwlink/?LinkId=261837)

## <a name="BKMK_Example__The_Y2K_bug"></a>Příklad: Chyba Y2K
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

 Testování této metody je obzvláště problematické, protože program závisí na `DateTime.Now`, metodě, která závisí na hodinách počítače, nedeterministické metodě závislé na prostředí. Kromě toho `DateTime.Now` je statická vlastnost, takže typ zástupné procedury se tady nedá použít. Tento problém je příznaky potíží s izolací při testování částí: programy, které přímo volají rozhraní API pro databáze, komunikují s webovými službami a tak dále, je obtížné testování částí, protože jejich logika závisí na prostředí.

 Toto je použití typy překrytí. Typy překrytí poskytují mechanismus pro vyhlídku libovolné metody .NET k delegátovi definovanému uživatelem. Typy překrytí jsou kódu generovaných generátor falešného a delegáty, které říkáme typy překrytí, používají k určení implementací nových metod.

 Následující testovací ukazuje, jak používat překrývající typ `ShimDateTime`, poskytnout vlastní implementaci DateTime.Now:

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

## <a name="BKMK_Fakes_requirements"></a>Jak používat překrytí

### <a name="AddFakes"></a> Přidání napodobeniny sestavení

1. V Průzkumník řešení rozbalte **odkazy**projektu testování částí.

    - Pokud pracujete v Visual Basic, musíte vybrat **Zobrazit všechny soubory** na panelu nástrojů Průzkumník řešení, aby se zobrazil seznam odkazů.

2. Vyberte sestavení, která obsahuje definice třídy, pro které chcete vytvořit Překryvné ovladače. Například pokud chcete překrýt data a času, vyberte System. dll.

3. V místní nabídce zvolte **přidat napodobeniny sestavení**.

### <a name="ShimsContext"></a> Použití ShimsContext
 Pokud používáte typy překrytí v rozhraní testování částí, musíte zabalit testovací kód ve `ShimsContext` řídit dobu životnosti vašeho překrytí. Pokud to nepotřebujeme, překrytí by mělo být poslední, dokud se doména AppDomain nevypne. Nejjednodušší způsob, jak vytvořit `ShimsContext` je pomocí statické `Create()` způsob, jak je znázorněno v následujícím kódu:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}

```

 Je velmi důležité, aby každý kontext překrytí správně odstranil. Jako říci, vždy volejte `ShimsContext.Create` uvnitř `using` příkaz k zajištění řádné vymazání registrované překrytí. Například může zaregistrovat překrytí pro testovací metodu, která nahrazuje `DateTime.Now` metoda s delegátem, která vždy vrátí 1 z ledna 2000. Pokud zapomenete vymazat shimu registrované v testovací metodě, zbytek testovacího běhu by vždy vrátí hodnotu prvním z ledna 2000 jako DateTime.Now. To může být suprising a matoucí.

### <a name="WriteShims"></a> Napsat test s překrytími
 V kódu testu, Vložit *odklonit* pro metodu, kterou chcete simulovat. Příklad:

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

 Názvy tříd překrytí jsou tvořeny vložením prefixu `Fakes.Shim` k původnímu názvu typu.

 Překrytí pracovní vložením *soubory balíčku detours* do kódu aplikace v rámci testu. Bez ohledu na to dojde k volání na původní metodu, Fakes systém provede náhradní proces, takže místo volání real – metoda je volána kód shim.

 Všimněte si, že soubory balíčku detours se vytvoří a odstraní v době běhu. Je nutné vytvořit vždy náhradního procesu v rámci životnosti `ShimsContext`. Když je odstraněn, se odeberou všechny překrytí, který jste vytvořili, zatímco byla aktivní. Je nejlepší způsob, jak to provést uvnitř `using` příkazu.

 Můžete se setkat sestavení chyba s informacemi o tom, že obor názvů rozhraní Fakes neexistuje. Tato chyba se zobrazí někdy, když existují další chyby při kompilaci. Odstraňte ostatní chyby a bude zmizí.

## <a name="BKMK_Shim_basics"></a> Překrytí pro různé druhy metod
 Typy překrytí umožňují nahradit libovolnou metodu .NET, včetně statických metod nebo nevirtuálních metodách, s vlastní delegáty.

### <a name="BKMK_Static_methods"></a> Statické metody
 Vlastnosti připojení překrytí pro statické metody jsou umístěny v typu překrytí. Každá vlastnost má pouze setter, který slouží k připojení k cílové metody delegáta. Mějme například třídy `MyClass` statickou metodou `MyMethod`:

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

 Doporučujeme připojit překrytí, aby `MyMethod` , která vždy vrátí hodnotu 5:

```csharp
// unit test code
ShimMyClass.MyMethod = () =>5;
```

### <a name="BKMK_Instance_methods__for_all_instances_"></a> Instance metody (pro všechny instance)
 Podobně pro statické metody, metody instance můžete překrýt pro všemi instancemi. Vlastnosti připojení těchto překrytí jsou umístěny ve vnořených typech AllInstances, aby nedocházelo k záměnám s názvem. Mějme například třídy `MyClass` s metodou instance `MyMethod`:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

 Můžete připojit k překrytí `MyMethod` , která vždy vrátí hodnotu 5, bez ohledu na to, instance:

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

 Generovaný typ struktury ShimMyClass bude vypadat jako v následujícím kódu:

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

 Všimněte si, že napodobenin v tomto případě předává instancí modulu runtime jako první argument delegáta.

### <a name="BKMK_Instance_methods__for_one_instance_"></a> Instance metody (pro jednu instanci modulu runtime)
 Instance metody lze také překrýt podle různých delegáty, založené na straně příjmu volání. Díky tomu stejné instance metoda může mít jiné chování za instanci typu. Vlastnosti, které chcete nastavit tyto překrytí jsou metody instance samotného typu překrytí. Každá instance překrývající typ je také přidružen nezpracovaná instanci překryté typu.

 Mějme například třídy `MyClass` s metodou instance `MyMethod`:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

 Můžeme nastavit dva typy překrytí MyMethod tak, že první z nich vždy vrátí hodnotu 5 a druhá vždy vrátí 10:

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

 Generovaný typ struktury ShimMyClass bude vypadat jako v následujícím kódu:

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

 Skutečný typ metodám instance je přístupný prostřednictvím vlastnosti Instance:

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

 Překrývající typ má také implicitní převod na typ překryté, takže můžete obvykle stačí použít typ překrytí, jako je:

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime
                         // instance
```

### <a name="BKMK_Constructors"></a> Konstruktory
 Aby bylo možné připojit typy překrytí na budoucí objekty můžete také překrýt konstruktory. Každý konstruktor je vystavena jako statickou metodu konstruktor v typu překrytí. Mějme například třída `MyClass` se konstruktor, který přebírá celé číslo:

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

 Nastavíme typ překrytí konstruktoru tak, že každá další instance vrátí -5, když uživatel vyvolá získá hodnotu, bez ohledu na hodnotu v konstruktoru:

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

 Všimněte si, že každý typ překrytí zveřejňuje dva konstruktory. Výchozí konstruktor byste měli použít, když je nezbytné nové instanci a konstruktor, který přebírá překryté instanci jako argument by měly být použity v překrytí pro konstruktor:

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

### <a name="BKMK_Base_members"></a> Základní členové
 Překrytí vlastností základních členů je možný vytváření překrytí pro základní typ a předáním instance podřízené jako parametr do konstruktoru třídy základní překrytí.

 Mějme například třídy `MyBase` s metodou instance `MyMethod` a podtyp `MyChild`:

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}

```

 Můžeme nastavit překrytí `MyBase` vytvořením nového `ShimMyBase` překrytí:

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

 Všimněte si, že je podřízený typ překrytí implicitně převeden na podřízené instance, kdy jako parametr předán konstruktoru základní překrytí.

 Generovaný typ struktury ShimMyChild a ShimMyBase vypadá podobně jako následující kód:

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

### <a name="BKMK_Static_constructors"></a> Statické konstruktory
 Typy překrytí vystavit statickou metodu `StaticConstructor` na kód shim statického konstruktoru typu. Vzhledem k tomu, že statické konstruktory jsou prováděny pouze jednou, je nutné zajistit, aby bylo překrytí nakonfigurováno před jakýmkoli členem typu.

### <a name="BKMK_Finalizers"></a> Finalizační metody
 Napodobeniny nepodporují finalizační metody.

### <a name="BKMK_Private_methods"></a> Privátní metody
 Generátor falešného kódu vytvoří vlastnosti překrytí pro privátní metody, které mají pouze viditelné typy v signatuře, tj. typy parametrů a návratový typ.

### <a name="BKMK_Binding_interfaces"></a> Vazba rozhraní
 Když překryté typ implementuje rozhraní, generátor kódu generuje metodu, která umožňuje vytvořit vazbu všech členů z rozhraní najednou.

 Mějme například třídy `MyClass` , který implementuje `IEnumerable<int>`:

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}

```

 Jsme překrýt implementace `IEnumerable<int>` v MyClass pomocí volání metody Bind:

```csharp
// unit test code
var shimMyClass = new ShimMyClass();
shimMyClass.Bind(new List<int> { 1, 2, 3 });

```

 Generovaný typ struktury ShimMyClass vypadá podobně jako následující kód:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public ShimMyClass Bind(IEnumerable<int> target) {
        ...
    }
}

```

## <a name="BKMK_Changing_the_default_behavior"></a>Změna výchozího chování
 Každý generovaný překrývající typ obsahuje instanci `IShimBehavior` prostřednictvím rozhraní `ShimBase<T>.InstanceBehavior` vlastnost. Chování slouží pokaždé, když klient volá člen instance, která nebyla výslovně překrýt.

 Pokud chování nebylo explicitně nastaveno, bude použita instance vrácená vlastností static `ShimsBehaviors.Current`. Ve výchozím nastavení, vrátí tato vlastnost chování, které se vyvolá `NotImplementedException` výjimky.

 Toto chování můžete kdykoli změnit tak, že nastavíte `InstanceBehavior` vlastnost na jakoukoli instanci překrytí. Například následující fragment kódu změní překrytí pro chování, které nic nedělá nebo vrací výchozí hodnotu návratového typu – to znamená, default(T):

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;

```

 Chování lze také změnit globálně pro všechny instance překryté pro kterou `InstanceBehavior` vlastnost nebyla nastavena explicitně nastavením statické `ShimsBehaviors.Current` vlastnost:

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimsBehaviors.Current =
    ShimsBehaviors.DefaultValue;

```

## <a name="BKMK_Detecting_environment_accesses"></a>Zjišťování přístupů k prostředí
 Je možné připojit chování u všech členů, včetně statických metod určitého typu pomocí přiřazení `ShimsBehaviors.NotImplemented` chování statickou vlastnost `Behavior` pro odpovídající typ překrytí:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();

```

## <a name="BKMK_Concurrency"></a> souběžnost
 Typy překrytí se vztahují na všechna vlákna v doméně AppDomain a nemají spřažení vláken. To je důležité skutečnosti, pokud máte v plánu pomocí nástroje test runner, které podporují souběžnosti: zahrnující typy překrytí testy nelze spustit souběžně. Tuto vlastnost neenfored modulem runtime napodobeniny.

## <a name="BKMK_Calling_the_original_method_from_the_shim_method"></a>Volání původní metody z metody Shim
 Představte si, že jsme chtěli po ověření názvu souboru předaný metodě skutečně vypsání textu do systému souborů. V takovém případě by chcete volat metodu původní uprostřed metodu překrytí.

 První postup pro vyřešení tohoto problému je zabalit volání na původní metodu pomocí delegáta a `ShimsContext.ExecuteWithoutShims()` stejně jako v následujícím kódu:

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

 Další možností je nastavit překrytí, aby s hodnotou null, zavolejte metodu původní a obnovení překrytí.

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

## <a name="BKMK_Limitations"></a> Omezení
 Překrytí nelze použít na všechny typy z knihovny základních tříd .NET **mscorlib** a **systému**.

## <a name="external-resources"></a>Externí zdroje

### <a name="guidance"></a>Doprovodné materiály
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 2: testování částí: testování uvnitř](https://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Viz také
 [Izolace testovaného kódu s Microsoftem falešného](../test/isolating-code-under-test-with-microsoft-fakes.md) [blogu Petra Provost: Video překrytí sady Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2) [(1H16): testování testovatelné kódu s napodobeninami v aplikaci Visual Studio 2012](https://go.microsoft.com/fwlink/?LinkId=261837)
