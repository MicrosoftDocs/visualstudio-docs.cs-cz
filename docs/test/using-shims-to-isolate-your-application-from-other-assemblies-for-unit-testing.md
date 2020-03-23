---
title: Použití podili, které izolují aplikaci pro testování částí.
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 480283b4f86f28fdedfb38687682fcee4e67646e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585532"
---
# <a name="use-shims-to-isolate-your-app-for-unit-testing"></a>Použití překrytí k izolátí aplikace pro testování částí

**Typy překrytí** jsou jednou ze dvou technologií, které rozhraní Microsoft Fakes Framework používá k tomu, aby vám umožní izolovat testované součásti od prostředí. Překrytí přesměrovat volání na konkrétní metody kódu, který napíšete jako součást testu. Mnoho metod vrátit různé výsledky v závislosti na externí podmínky, ale překrytí je pod kontrolou testu a může vrátit konzistentní výsledky při každém volání. To usnadňuje psaní testů.

Pomocí *překrytí* izolovat kód z sestavení, které nejsou součástí vašeho řešení. Chcete-li od sebe izolovat součásti řešení, použijte *zástupné procedury*.

Přehled a pokyny pro rychlý start najdete v [tématu izolovat kód testovaný s Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

**Požadavky**

- Visual Studio Enterprise
- Projekt rozhraní .NET Framework

> [!NOTE]
> Standardní projekty .NET nejsou podporovány.

## <a name="example-the-y2k-bug"></a>Příklad: Chyba Y2K

Zvažte metodu, která vyvolá výjimku 1.

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Testování této metody je problematické, `DateTime.Now`protože program závisí na metodě , která závisí na hodinách počítače, nedeterministické metodě závislé na prostředí. Kromě toho `DateTime.Now` je statická vlastnost, takže typ se zakázaným inzerováním nelze použít zde. Tento problém je symptomatický problém izolace v testování částí: programy, které přímo volat do databáze rozhraní API, komunikovat s webovými službami a tak dále, je obtížné testování částí, protože jejich logika závisí na prostředí.

To je místo, kde by měly být použity typy překrytí. Typy překrytí poskytují mechanismus objížďka libovolnou metodu .NET uživatelem definované delegáta. Typy překrytí jsou generovány kódem generátoru Fakes a používají delegáty, které nazýváme typy překrytí, k určení nových implementací metody.

Následující test ukazuje, jak používat typ `ShimDateTime`překrytí, , poskytnout vlastní implementaci DateTime.Now:

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

## <a name="how-to-use-shims"></a>Jak používat podložky

Nejprve přidejte sestavení Fakes:

1. V **Průzkumníku řešení**rozbalte uzel **Reference** projektu testování částí.

   - Pokud pracujete v jazyce Visual Basic, vyberte **Zobrazit všechny soubory** na panelu nástrojů Průzkumník **řešení,** abyste zobrazili uzel **Reference.**

2. Vyberte sestavení, které obsahuje definice tříd, pro které chcete vytvořit překrytí. Chcete-li například překrytí **datačasu**, vyberte **položku System.dll**.

3. V místní nabídce zvolte **Přidat falešnou sestavu**.

### <a name="use-shimscontext"></a>Použití kontextu ShimsContext

Při použití typů překrytí v rámci testování částí `ShimsContext` zabalit testovací kód v řídit životnost překrytí. V opačném případě překrytí bude trvat, dokud AppDomain vypnout. Nejjednodušší způsob, jak `ShimsContext` vytvořit, je `Create()` pomocí statické metody, jak je znázorněno v následujícím kódu:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

Je důležité správně zlikvidovat každý kontext překrytí. Jako pravidlo, volat `ShimsContext.Create` uvnitř `using` prohlášení k zajištění řádného vymazání registrovaných podměn. Můžete například zaregistrovat překrytí pro testovací metodu, která nahradí metodu `DateTime.Now` delegátem, který vždy vrátí první z ledna 2000. Pokud zapomenete vymazat registrované překrytí v testovací metodě, zbytek zkušebního běhu vždy vrátí první `DateTime.Now` z ledna 2000 jako hodnotu. To může být překvapivé a matoucí.

### <a name="write-a-test-with-shims"></a>Napsat test s podložkami

Do testovacího kódu vložte *objížďku* pro metodu, kterou chcete falešnou. Například:

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

Názvy tříd překrytí jsou `Fakes.Shim` tvořeny předponou na původní název typu.

Překrytí práce vložením *objížďky* do kódu aplikace testované. Všude tam, kde dojde k volání původní metody, systém Fakes provede objížďku, takže místo volání skutečné metody je volán kód překrytí.

Všimněte si, že objížďky jsou vytvořeny a odstraněny za běhu. Musíte vždy vytvořit objížďku v `ShimsContext`rámci života . Po vyřazení budou odebrány všechny překrytí, které jste vytvořili během jeho aktivní hodu. Nejlepší způsob, jak to `using` udělat, je uvnitř prohlášení.

Může se zobrazit chyba sestavení oznamující, že obor názvů Fakes neexistuje. Tato chyba se někdy zobrazí, pokud existují jiné chyby kompilace. Opravit další chyby a zmizí.

## <a name="shims-for-different-kinds-of-methods"></a>Podložky pro různé druhy metod

Typy překrytí umožňují nahradit libovolnou metodu .NET, včetně statických metod nebo nevirtuálních metod, vlastními delegáty.

### <a name="static-methods"></a>Statické metody

Vlastnosti, které mají být připojeny k statickým metodám, jsou umístěny v překrytí. Každá vlastnost má pouze setter, který lze použít k připojení delegáta k cílové metody. Například dané třídy `MyClass` se `MyMethod`statickou metodou :

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

Můžeme připojit podložku, `MyMethod` která vždy vrátí 5:

```csharp
// unit test code
ShimMyClass.MyMethod = () => 5;
```

### <a name="instance-methods-for-all-instances"></a>Metody instance (pro všechny instance)

Podobně jako statické metody mohou být metody instance pro všechny instance shimmed. Vlastnosti pro připojení těchto překrytí jsou umístěny v nosné typu s názvem AllInstances, aby se zabránilo záměně. Například dané třídy `MyClass` s `MyMethod`metodou instance :

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

K překrytí můžete `MyMethod` připojit, která vždy vrátí hodnotu 5, bez ohledu na instanci:

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

Generovaný typ struktura ShimMyClass vypadá jako následující kód:

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

Všimněte si, že Fakes předá instanci runtime jako první argument delegáta v tomto případě.

### <a name="instance-methods-for-one-runtime-instance"></a>Metody instance (pro jednu instanci runtime)

Instance metody mohou být také shimmed různými delegáty, na základě příjemce volání. To umožňuje stejnou metodu instance mít různé chování pro instanci typu. Vlastnosti pro nastavení těchto překrytí jsou instance metody překrytí samotného typu. Každý typ vytvoření instance překrytí je také spojen s nezpracovaná instance typu shimmed.

Například dané třídy `MyClass` s `MyMethod`metodou instance :

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Můžeme nastavit dva typy překrytí MyMethod tak, že první z nich vždy vrátí 5 a druhý vždy vrátí 10:

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

Generovaný typ struktura ShimMyClass vypadá jako následující kód:

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

Skutečná instance typu shimmed je přístupná prostřednictvím vlastnosti Instance:

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

Typ překrytí má také implicitní převod na typ shimmed, takže obvykle můžete jednoduše použít typ překrytí tak, jak je:

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime instance
```

### <a name="constructors"></a>Konstruktory

Konstruktory lze také shimmed za účelem připojení typy překrytí na budoucí objekty. Každý konstruktor je vystaven jako statická metoda Konstruktor v typu překrytí. Například dané třídy `MyClass` s konstruktorem s celé číslo:

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Nastavíme typ překrytí konstruktoru tak, aby každá budoucí instance vrátí -5 při vyvolání getter value, bez ohledu na hodnotu v konstruktoru:

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

Každý typ překrytí vystavuje dva konstruktory. Výchozí konstruktor by měl být použit, když je potřeba novou instanci, zatímco konstruktor s shimmed instance jako argument by měl být použit v překrytí konstruktoru pouze:

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

Generovaná struktura typu ShimMyClass se podobá následujícímu kódu:

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

### <a name="base-members"></a>Členové základny

Vlastnosti překrytí základních členů lze přistupovat vytvořením překrytí pro základní typ a předáním podřízené instance jako parametr konstruktoru základní třídy překrytí.

Například dané třídy `MyBase` s `MyMethod` metodou instance `MyChild`a podtypem :

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

Můžeme nastavit podložku `MyBase` vytvořením nové `ShimMyBase` houštiny:

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

Všimněte si, že podřízený typ překrytí je implicitně převeden na podřízenou instanci, když je předán jako parametr základnímu konstruktoru překrytí.

Generovaná struktura typů ShimMyChild a ShimMyBase se podobá následujícímu kódu:

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

Typy překrytí vystavit `StaticConstructor` statickou metodu překrytí statický konstruktor typu. Vzhledem k tomu, že statické konstruktory jsou spuštěny pouze jednou, je třeba se ujistit, že překrytí je nakonfigurován před libovolný člen typu je přístupný.

### <a name="finalizers"></a>Finalizační metody

Finalizační metody nejsou podporovány ve fakes.

### <a name="private-methods"></a>Soukromé metody

Generátor kódu Fakes vytvoří vlastnosti překrytí pro soukromé metody, které mají pouze viditelné typy v podpisu, to znamená, že typy parametrů a návratový typ viditelné.

### <a name="binding-interfaces"></a>Vazby rozhraní

Když shimmed typ implementuje rozhraní, generátor kódu vydává metodu, která umožňuje svázat všechny členy z tohoto rozhraní najednou.

Například dané třídy, `MyClass` `IEnumerable<int>`která implementuje :

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}
```

Můžete překrytí implementace `IEnumerable<int>` v MyClass voláním Bind metoda:

```csharp
// unit test code
var shimMyClass = new ShimMyClass();
shimMyClass.Bind(new List<int> { 1, 2, 3 });
```

Generovaná struktura typu ShimMyClass se podobá následujícímu kódu:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public ShimMyClass Bind(IEnumerable<int> target) {
        ...
    }
}
```

## <a name="change-the-default-behavior"></a>Změna výchozího chování

Každý generovaný typ překrytí `IShimBehavior` obsahuje instanci rozhraní prostřednictvím vlastnosti. `ShimBase<T>.InstanceBehavior` Chování se používá vždy, když klient volá člen instance, který nebyl explicitně shimmed.

Pokud chování nebylo explicitně nastaveno, použije instanci vrácenou statickou `ShimsBehaviors.Current` vlastností. Ve výchozím nastavení tato vlastnost vrátí `NotImplementedException` chování, které vyvolá výjimku.

Toto chování lze kdykoli změnit `InstanceBehavior` nastavením vlastnosti na libovolné podidře. Například následující úryvek změní překrytí na chování, které neprovede žádné funkce, nebo `default(T)`vrátí výchozí hodnotu návratového typu – to znamená :

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;
```

Chování lze také změnit globálně pro všechny shimmed `InstanceBehavior` instance, pro které vlastnost `ShimsBehaviors.Current` nebyla explicitně nastavena nastavením statické vlastnosti:

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimsBehaviors.Current = ShimsBehaviors.DefaultValue;
```

## <a name="detect-environment-accesses"></a>Detekce přístupů k prostředí

Je možné připojit chování ke všem členům, včetně statických metod, `ShimsBehaviors.NotImplemented` určitého typu `Behavior` přiřazením chování statickou vlastnostodpovídající překrytí typu:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

## <a name="concurrency"></a>Souběžnost

Typy překrytí platí pro všechna vlákna v AppDomain a nemají spřažení podprocesů. To je důležitý fakt, pokud máte v plánu použít testovací běžec, který podporuje souběžnost. Testy zahrnující typy překrytí nelze spustit souběžně. Tato vlastnost není vynucena runtime Fakes.

## <a name="call-the-original-method-from-the-shim-method"></a>Volání původní metody z metody překrytí

Představte si, že chcete napsat text do systému souborů po ověření názvu souboru předané metodě. V takovém případě byste volání původní metody uprostřed metody překrytí.

První přístup k vyřešení tohoto problému je zabalit volání původní `ShimsContext.ExecuteWithoutShims()`metody pomocí delegáta a , jako v následujícím kódu:

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

Jiný přístup je nastavit překrytí na hodnotu null, volání původní metody a obnovení překrytí.

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

## <a name="systemenvironment"></a>System.Životní prostředí

Chcete-li <xref:System.Environment?displayProperty=fullName>překrytí , přidejte následující obsah do souboru mscorlib.fakes za element **Assembly:**

```xml
<ShimGeneration>
    <Add FullName="System.Environment"/>
</ShimGeneration>
```

Po opětovném sestavení řešení jsou k <xref:System.Environment?displayProperty=fullName> dispozici metody a vlastnosti ve třídě, které lze překrytí, například:

```csharp
System.Fakes.ShimEnvironment.GetCommandLineArgsGet = ...
```

## <a name="limitations"></a>Omezení

Překrytí nelze použít na všechny typy z knihovny základní třídy .NET **mscorlib** a **systém**.

## <a name="see-also"></a>Viz také

- [Izolace testovaného kódu pomocí Napodobenin Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Peter Provost blog: Visual Studio 2012 podložky](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Video (1h16): Testování netestovatelného kódu s padělky ve Visual Studiu 2012](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
