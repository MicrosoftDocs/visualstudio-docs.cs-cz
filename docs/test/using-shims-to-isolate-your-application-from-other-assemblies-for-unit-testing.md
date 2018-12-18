---
title: Izolace aplikace pro testování částí pomocí Překryvné ovladače
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b94852b15891566bdfc38dd3fd8de9e706f38737
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065607"
---
# <a name="use-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>Izolace aplikace od jiných sestavení pomocí testů shim za účelem testování částí

**Typy překrýt** jsou jedním ze dvou technologií, které architektura Fakes Microsoft používá k vám umožní snadno izolovat komponenty v rámci testu z prostředí. Překrytí rozdělení volání konkrétní metody do kódu, který píšete v rámci testu. Mnoho metod vrátit různé výsledky závislé na externích podmínky, ale překrytí je pod kontrolou vašeho testu a může vrátit konzistentní výsledky při každém volání. Jednodušší testy k zápisu.

Překryvné ovladače použijte k izolování váš kód ze sestavení, které nejsou součástí vašeho řešení. Součástí vašeho řešení od sebe navzájem izolovat, doporučujeme použít zástupné procedury.

Přehled a rychlý start pokyny, najdete v části [izolace testovaného kódu pomocí Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)

**Požadavky**

-   Visual Studio Enterprise
-   Rozhraní .NET Framework projektu

> [!NOTE]
> Projekty .NET standard teď nejsou podporovány.

## <a name="example-the-y2k-bug"></a>Příklad: Určená chyb

Pojďme se na metodu, která vyvolá výjimku v 1. ledna 2000:

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Testování tato metoda je problematický, protože program závisí na `DateTime.Now`, metodu, která závisí na počítači uživatele hodiny, prostředí závislé Nedeterministický metody. Kromě toho `DateTime.Now` je statická vlastnost, typ podložení se tady nedá použít. Tento problém je napraveny izolace problém v testování částí: testování programy, které je těžké jednotky přímo volat rozhraní API, databáze komunikovat s webovými službami a tak dále, protože jejich logiku závisí na prostředí.

Toto je použití typy překrytí. Typy překrytí poskytují mechanismus pro předání libovolnou metodu .NET do uživatelsky definovaného delegáta. Typy překrytí jsou kódu generovaných generátor falešného a delegáty, které říkáme typy překrytí, používají k určení implementací nových metod.

Následující testovací ukazuje, jak používat překrývající typ `ShimDateTime`, poskytnout vlastní implementaci DateTime.Now:

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

##  <a name="how-to-use-shims"></a>Jak použít překrytí

###  <a name="AddFakes"></a> Přidání napodobeniny sestavení

1.  V **Průzkumníka řešení**, rozbalte položku projektu jednotkového testu **odkazy**.

    -   Pokud pracujete v jazyce Visual Basic, vyberte **zobrazit všechny soubory** v **Průzkumníka řešení** nástrojů, chcete-li zobrazit **odkazy** uzlu.

2.  Vyberte sestavení, která obsahuje definice třídy, pro které chcete vytvořit Překryvné ovladače. Například, pokud chcete překrýt **data a času**vyberte **System.dll**.

3.  V místní nabídce zvolte **přidat napodobeniny sestavení**.

###  <a name="ShimsContext"></a> Použití ShimsContext

Pokud používáte typy překrytí v rozhraní testování částí, musíte zabalit testovací kód ve `ShimsContext` řídit dobu životnosti vašeho překrytí. Pokud nebyla potřeba se to, by vaše překrytí naposledy až do ukončení domény aplikace. Nejjednodušší způsob, jak vytvořit `ShimsContext` je pomocí statické `Create()` způsob, jak je znázorněno v následujícím kódu:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

Je velmi důležité správně dispose každý kontext překrytí. Jako říci, vždy volejte `ShimsContext.Create` uvnitř `using` příkaz k zajištění řádné vymazání registrované překrytí. Například může zaregistrovat překrytí pro testovací metodu, která nahrazuje `DateTime.Now` metoda s delegátem, která vždy vrátí 1 z ledna 2000. Pokud zapomenete vymazat shimu registrované v testovací metodě, zbytek testovacího běhu by vždy vrátí hodnotu prvním z ledna 2000 jako DateTime.Now. To může být překvapivé a chaoticky.

###  <a name="WriteShims"></a> Napsat test s překrytími

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

##  <a name="BKMK_Shim_basics"></a> Překrytí pro různé druhy metod

Typy překrytí umožňují nahradit libovolnou metodu .NET, včetně statických metod nebo nevirtuálních metodách, s vlastní delegáty.

###  <a name="BKMK_Static_methods"></a> Statické metody

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

###  <a name="BKMK_Instance_methods__for_all_instances_"></a> Instance metody (pro všechny instance)

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

###  <a name="BKMK_Instance_methods__for_one_instance_"></a> Instance metody (pro jednu instanci modulu runtime)

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

###  <a name="BKMK_Constructors"></a> Konstruktory

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

Každý typ překrytí poskytuje dva konstruktory. Výchozí konstruktor byste měli použít, když je nezbytné nové instanci a konstruktor, který přebírá překryté instanci jako argument by měly být použity v překrytí pro konstruktor:

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

Generovaný typ struktury ShimMyClass vypadá podobně jako následující kód:

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

###  <a name="BKMK_Base_members"></a> Základní členové

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

###  <a name="BKMK_Static_constructors"></a> Statické konstruktory

Typy překrytí vystavit statickou metodu `StaticConstructor` na kód shim statického konstruktoru typu. Protože statické konstruktory jsou spouštěny, když potřebujete pouze, ujistěte se, že shimu je dřív, než přistupuje kteréhokoli člena typu.

###  <a name="BKMK_Finalizers"></a> Finalizační metody

Napodobeniny nepodporují finalizační metody.

###  <a name="BKMK_Private_methods"></a> Privátní metody

Generátor falešného kódu vytvoří vlastnosti překrytí pro privátní metody, které mají pouze viditelné typy v podpisu, to znamená, typy parametrů a návratový typ viditelný.

###  <a name="BKMK_Binding_interfaces"></a> Vazba rozhraní

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

##  <a name="change-the-default-behavior"></a>Změnit výchozí chování

Každý generovaný překrývající typ obsahuje instanci `IShimBehavior` prostřednictvím rozhraní `ShimBase<T>.InstanceBehavior` vlastnost. Chování slouží pokaždé, když klient volá člen instance, která nebyla výslovně překrýt.

Pokud chování nebylo nastaveno explicitně, použije instance vrácené statickou `ShimsBehaviors.Current` vlastnost. Ve výchozím nastavení, vrátí tato vlastnost chování, které se vyvolá `NotImplementedException` výjimky.

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

##  <a name="detect-environment-accesses"></a>Zjištění přístupy do prostředí

Je možné připojit chování u všech členů, včetně statických metod určitého typu pomocí přiřazení `ShimsBehaviors.NotImplemented` chování statickou vlastnost `Behavior` pro odpovídající typ překrytí:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

##  <a name="BKMK_Concurrency"></a> souběžnost

Typy překrytí platí pro všechna vlákna v doméně aplikace a nemají spřažení vláken. To je důležité skutečnosti, pokud máte v plánu pomocí nástroje test runner, které podporují souběžnosti: zahrnující typy překrytí testy nelze spustit souběžně. Tato vlastnost není vynucena napodobeninu knihovny runtime.

##  <a name="call-the-original-method-from-the-shim-method"></a>Volat metodu původní metodou překrytí

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

##  <a name="BKMK_Limitations"></a> Omezení

Překrytí nelze použít na všechny typy z knihovny základních tříd .NET **mscorlib** a **systému**.

## <a name="see-also"></a>Viz také:

- [Izolace testovaného kódu pomocí Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Peter Provost blog: překrytí Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Video (1 hodina 16): testování untestable kódu pomocí zástupného rozhraní v sadě Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837)
