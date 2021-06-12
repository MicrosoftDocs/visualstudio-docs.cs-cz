---
title: Izolace aplikace pomocí shimů (testování částí)
description: Naučte se používat typy pře shimů k přesměrování volání konkrétních metod kódu, který napíšete jako součást testu. Pře shim může při každém volání vracet konzistentní výsledky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 72a976ccd487abdfa2c6501c0dcafee07dc5f4ae
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042857"
---
# <a name="use-shims-to-isolate-your-app-for-unit-testing"></a>Izolace aplikace pro testování částí pomocí přetýmků

**Pře shimové** typy jsou jednou ze dvou technologií, které Microsoft Fakes Framework používá k izolaci testových komponent od prostředí. Přemísti odklání volání konkrétních metod kódu, který napíšete jako součást testu. Mnoho metod vrací různé výsledky závislé na externích podmínkách, ale pře shim je pod kontrolou testu a může vracet konzistentní výsledky při každém volání. To usnadňuje psaní testů.

Pomocí *přetáků* izolovat kód od sestavení, která nejsou součástí vašeho řešení. Chcete-li izolovat komponenty řešení od sebe navzájem, použijte *zástupné procedury*.

Přehled a pokyny pro rychlý start najdete v tématu Izolace [testového](../test/isolating-code-under-test-with-microsoft-fakes.md)kódu pomocí Microsoft Fakes .

**Požadavky**

- Visual Studio Enterprise
- Projekt .NET Framework projektu
::: moniker range=">=vs-2019"
- Podpora projektů ve stylu .NET Core, .NET 5.0 a SDK ve verzi Preview ve verzi Visual Studio 2019 Update 6 je ve výchozím nastavení povolená v aktualizaci Update 8. Další informace najdete v tématu [Microsoft Fakes pro projekty .NET Core a projekty ve stylu sady SDK.](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects)
::: moniker-end

## <a name="example-the-y2k-bug"></a>Příklad: Chyba Y2K

Představte si metodu, která 1. ledna 2000 vyvolá výjimku:

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Testování této metody je problematické, protože program závisí na metodě , která závisí na hodinách počítače, ne deterministické metodě závislé na `DateTime.Now` prostředí. Objekt je navíc statická vlastnost, takže zde nelze `DateTime.Now` použít typ zástupné procedury. Tento problém spočívá v problému s izolací při testování částí: programy, které přímo volají databázová rozhraní API, komunikují s webovými službami atd., se těžko testují, protože jejich logika závisí na prostředí.

Zde by se měly používat typy pře shimů. Pře shimové typy poskytují mechanismus pro obchádování jakékoli metody rozhraní .NET na delegáta definovaného uživatelem. Shimové typy jsou kódem generovaným generátorem Fakes a používají delegáty, kterým říkáme typy shimů, k určení nových implementací metod.

Následující test ukazuje, jak použít typ pře shimu `ShimDateTime` k poskytnutí vlastní implementace DateTime.Now:

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

## <a name="how-to-use-shims"></a>Jak používat pře shimy

Nejprve přidejte sestavení Fakes:

1. V **Průzkumník řešení**, 
    - U staršího .NET Framework Project (bez stylu sady SDK) rozbalte uzel **Odkazy** projektu testování částí.
    ::: moniker range=">=vs-2019"
    - V případě projektu ve stylu sady SDK, který cílí na .NET Framework, .NET  Core nebo .NET 5.0, rozbalte uzel Závislosti a v části Sestavení **,** **Projekty** nebo Balíčky vyhledejte sestavení, které chcete napodobenit. 
    ::: moniker-end
    - Pokud pracujete v pracovním Visual Basic, vyberte **Zobrazit** všechny soubory na panelu **Průzkumník řešení** panelu nástrojů a zobrazte **uzel** Odkazy.

2. Vyberte sestavení, které obsahuje definice tříd, pro které chcete vytvořit pře shimy. Pokud například chcete přetát **DateTime**, vyberte **System.dll**.

3. V místní nabídce zvolte Add **Fakes Assembly (Přidat sestavení Fakes).**

### <a name="use-shimscontext"></a>Použití ShimsContext

Při použití pře shimů v rozhraní testování částí zabalte testovací kód do , abyste ovládaly `ShimsContext` životnost pře shimů. Jinak by přetáčky trvaly, dokud se doména AppDomain nevypne. Nejjednodušší způsob, jak vytvořit `ShimsContext` objekt , je použít statickou `Create()` metodu , jak je znázorněno v následujícím kódu:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

Je důležité správně likvidovat každý kontext přemíste. Jako základní pravidlo volejte uvnitř příkazu , aby se zajistilo správné vymazání `ShimsContext.Create` `using` registrovaných pře shimů. Můžete například zaregistrovat pře shim pro testovací metodu, která nahradí metodu delegátem, který vždy vrátí první z `DateTime.Now` ledna 2000. Pokud zapomenete vymazat registrovaný shim v testovací metodě, zbytek testovacího běhu vždy vrátí první z ledna 2000 jako `DateTime.Now` hodnotu. To může být překvapivé a matoucí.

### <a name="write-a-test-with-shims"></a>Napsání testu pomocí pře shimů

Do testovacího kódu vložte *objížďku* pro metodu, kterou chcete napodobenovat. Příklad:

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

Názvy pře shimových tříd se směšují `Fakes.Shim` předponou k původnímu názvu typu.

Přetáčky fungují tak, *že do* kódu testované aplikace vloží obchádky. Bez ohledu na to, kde dojde k volání původní metody, provede systém Fakes objížďku, takže místo volání skutečné metody se volá váš kód shim.

Všimněte si, že za běhu se vytvoří a odstraní obchádky. Vždy musíte vytvořit obchádku v rámci životnosti `ShimsContext` . Po odstranění se odstraní všechny přešíčky, které jste vytvořili v době, kdy byl aktivní. Nejlepší způsob, jak to provést, je uvnitř `using` příkazu .

Může se zobrazit chyba sestavení s oznámením, že obor názvů Fakes neexistuje. Tato chyba se někdy zobrazí, když dojde k jiným chybám kompilace. Opravte ostatní chyby a zmizí.

## <a name="shims-for-different-kinds-of-methods"></a>Přetáčky pro různé druhy metod

Pře shimové typy umožňují nahradit jakoukoli metodu .NET, včetně statických nebo ne virtuálních metod, vlastními delegáty.

### <a name="static-methods"></a>Statické metody

Vlastnosti pro připojení pře shimů ke statickým metodám jsou umístěny v typu pře shim. Každá vlastnost má pouze setter, který lze použít k připojení delegáta k cílové metodě. Například na třídu se `MyClass` statickou metodou `MyMethod` :

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

Můžeme k zařízení připojit pře `MyMethod` shim, který vždy vrátí hodnotu 5:

```csharp
// unit test code
ShimMyClass.MyMethod = () => 5;
```

### <a name="instance-methods-for-all-instances"></a>Metody instance (pro všechny instance)

Podobně jako statické metody lze instance přetát pro všechny instance. Vlastnosti pro připojení těchto přehozů jsou umístěny do vnořeného typu s názvem AllInstances, aby nedocházelo k nejasnostem. Například na třídu s `MyClass` metodou instance `MyMethod` :

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Přetávku můžete připojit k `MyMethod` , která vždy vrátí hodnotu 5 bez ohledu na instanci:

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

Vygenerovaná struktura typu ShimMyClass vypadá jako následující kód:

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

Všimněte si, že Fakes předává instanci modulu runtime jako první argument delegáta v tomto případě.

### <a name="instance-methods-for-one-runtime-instance"></a>Metody instance (pro jednu instanci modulu runtime)

Metody instance lze také přenést různými delegáty v závislosti na příjemci volání. To umožňuje stejné metodě instance mít různé chování pro každou instanci typu. Vlastnosti pro nastavení těchto pře shimů jsou metody instancí samotného typu pře shim. Každý typ pře shimu s vytvořenou instancí je také přidružen k nezpracované instanci pře shimmovaného typu.

Například na třídu s `MyClass` metodou instance `MyMethod` :

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Můžeme nastavit dva typy pře shimů MyMethod tak, aby první vždy vrátil 5 a druhý vždy vrátil 10:

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

Vygenerovaná struktura typu ShimMyClass vypadá jako následující kód:

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

Instance skutečného přetmíděného typu je přístupná prostřednictvím vlastnosti Instance:

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

Typ pře shimu má také implicitní převod na přetácený typ, takže obvykle můžete jednoduše použít typ pře shimu, jak je:

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime instance
```

### <a name="constructors"></a>Konstruktory

Konstruktory lze také přetát, aby bylo možné připojit typy pře shimů k budoucím objektům. Každý konstruktor je vystavený jako konstruktor statické metody v typu překrytí. Například na třídu s `MyClass` konstruktorem, který přečítá celé číslo:

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Nastavili jsme typ pře shimu konstruktoru tak, aby každá budoucí instance při vyvolání metody Value getter bez ohledu na hodnotu v konstruktoru vrátila hodnotu -5:

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

Každý typ přetáčky zpřístupňuje dva konstruktory. Pokud je potřeba nová instance, měl by se použít výchozí konstruktor, zatímco konstruktor přetácené instance jako argument by měl být použit pouze v pře shimech konstruktoru:

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

Vygenerovaná struktura typu ShimMyClass se podobá následujícímu kódu:

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

### <a name="base-members"></a>Základní členy

K vlastnostem pře shimu základních členů lze získat přístup tak, že vytvoříte pře shim pro základní typ a předáte podřízené instanci jako parametr konstruktoru základní třídy shim.

Například pro třídu s `MyBase` metodou instance `MyMethod` a podtypem `MyChild` :

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

Pře shim můžeme nastavit `MyBase` tak, že vytvoříme nový `ShimMyBase` pře shim:

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

Všimněte si, že podřízený typ pře shimu je implicitně převeden na podřízené instance, pokud je předán jako parametr konstruktoru základního pře shimu.

Vygenerovaná struktura typu ShimMyChild a ShimMyBase vypadá podobně jako následující kód:

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

Pře shimové typy zpřístupňuje `StaticConstructor` statickou metodu pře shim statického konstruktoru typu. Vzhledem k tomu, že statické konstruktory jsou spouštěny pouze jednou, je nutné se ujistit, že je shim nakonfigurován před přístupem k libovolnému členu typu.

### <a name="finalizers"></a>Finalizační metody

Finalizační metody se ve napodobenině nepodporují.

### <a name="private-methods"></a>Soukromé metody

Generátor falešného kódu vytvoří vlastnosti překrytí pro privátní metody, které mají pouze viditelné typy v signatuře, to znamená, že typy parametrů a návratový typ jsou viditelné.

### <a name="binding-interfaces"></a>Rozhraní vazby

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

Můžete překrýt implementace v metodě `IEnumerable<int>` MyClass voláním metody bind:

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

Každý generovaný typ překrytí uchovává instanci `IShimBehavior` rozhraní prostřednictvím `ShimBase<T>.InstanceBehavior` Vlastnosti. Chování se používá vždy, když klient volá člen instance, který nebyl explicitně překryté.

Pokud chování nebylo explicitně nastaveno, použije instanci vrácenou statickou `ShimBehaviors.Current` vlastností. Ve výchozím nastavení tato vlastnost vrací chování, které vyvolá `NotImplementedException` výjimku.

Toto chování lze kdykoli změnit nastavením `InstanceBehavior` vlastnosti u jakékoli instance překrytí. Například následující fragment kódu změní překrytí na chování, které nedělá nic nebo vrátí výchozí hodnotu návratového typu – to znamená `default(T)` :

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimBehaviors.DefaultValue;
```

Chování se dá také globálně změnit pro všechny instance překryté, pro které se `InstanceBehavior` vlastnost explicitně nenastavuje, nastavením `ShimBehaviors.Current` vlastnosti static:

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimBehaviors.Current = ShimBehaviors.DefaultValue;
```

## <a name="detect-environment-accesses"></a>Detekovat přístup k prostředí

Je možné připojit chování ke všem členům, včetně statických metod určitého typu, přiřazením `ShimBehaviors.NotImplemented` chování statické vlastnosti `Behavior` odpovídajícího typu překrytí:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

## <a name="concurrency"></a>Souběžnost

Typy překrytí se vztahují na všechna vlákna v doméně AppDomain a nemají spřažení vláken. Toto je důležitý fakt, pokud plánujete použít Test Runner, který podporuje souběžnost. Testy zahrnující typy překrytí nemůžou běžet souběžně. Tato vlastnost není vynutila modulem runtime napodobeniny.

## <a name="call-the-original-method-from-the-shim-method"></a>Volání původní metody z metody Shim

Představte si, že chcete po ověření názvu souboru předaného do metody napsat text do systému souborů. V takovém případě byste měli zavolat původní metodu uprostřed metody Shim.

Prvním přístupem k vyřešení tohoto problému je zabalení volání původní metody pomocí delegáta a `ShimsContext.ExecuteWithoutShims()` , jak je uvedeno v následujícím kódu:

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

Do překrytí <xref:System.Environment?displayProperty=fullName> přidejte následující obsah do souboru mscorlib. napodobeniny po elementu **sestavení** :

```xml
<ShimGeneration>
    <Add FullName="System.Environment"/>
</ShimGeneration>
```

Po opětovném sestavení řešení jsou metody a vlastnosti ve <xref:System.Environment?displayProperty=fullName> třídě k dispozici pro překryté, například:

```csharp
System.Fakes.ShimEnvironment.GetCommandLineArgsGet = ...
```

## <a name="limitations"></a>Omezení

Překrytí nelze použít pro všechny typy z knihovny třídy Base rozhraní .NET **mscorlib** a **systém** v systému .NET Framework a v **System. Runtime** v rozhraní .NET Core nebo .NET 5,0.

## <a name="see-also"></a>Viz také

- [Izolace testovaného kódu pomocí Napodobenin Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Blog Petra Provost: překrytí sady Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Video (1h16): testování netestovaných kódů s napodobeninami v aplikaci Visual Studio 2012](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
