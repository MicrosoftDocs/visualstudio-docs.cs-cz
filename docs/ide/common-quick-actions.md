---
title: Běžné rychlé akce
description: Nejoblíbenější rychlé akce pro C# a Visual Basic, včetně opravy chybně napsaných klíčových slov nebo symbolů, řešení konfliktů sloučení, odstranění potřebných importů, generování typů, zavedení místních proměnných atd.
ms.date: 03/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: db7a3a550f6bfc1250679eeefa0ba3ec6291eef0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585519"
---
# <a name="common-quick-actions"></a>Běžné rychlé akce

Části v tomto tématu seznam některých běžných **rychlých akcí,** které jsou použitelné pro c# a visual basic kód. Tyto akce jsou *opravy kódu* pro diagnostiku kompilátoru nebo integrované [analyzátory platformy kompilátoru .NET](../code-quality/roslyn-analyzers-overview.md) v sadě Visual Studio.

## <a name="actions-that-fix-errors"></a>Akce, které opravují chyby

Rychlé akce v této části opravit chyby v kódu, který by způsobil selhání sestavení. Pokud jsou k dispozici rychlé akce k opravě chyby na řádku kódu, ikona, která se zobrazí na okraji nebo pod červenou vlnovkou, je žárovka s červeným "x".

![Ikona chyby a nabídka chyby Rychlé akce](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Oprava chybně napsaného symbolu nebo klíčového slova

Pokud omylem chybně napíšete typ nebo klíčové slovo v sadě Visual Studio, tato rychlá akce je automaticky opraví za vás. Tyto položky se zobrazí v nabídce žárovky jako **"Změnit "\<\<chybně napsané slovo>' na 'správné slovo> '.** Například:

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

| ID chyby | Příslušné jazyky |
| - | - |
| CS0103, BC30002 | C# a Visual Basic |

### <a name="resolve-git-merge-conflict"></a>Vyřešit konflikt sloučení git

Tyto rychlé akce umožňují vyřešit konflikty sloučení git "přijetím změny", která odebere konfliktní kód a značky.

```csharp
// Before
private void MyMethod()
{
    if (false)
    {

    }
}

// Take changes from 'HEAD'

// After
private void MyMethod()
{
    if (true)
    {

    }
}
```

| ID chyby | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| CS8300, BC37284 | C# a Visual Basic | Visual Studio 2017 verze 15.3 a novější |

## <a name="actions-that-remove-unnecessary-code"></a>Akce, které odeberou nepotřebný kód

### <a name="remove-unnecessary-usingsimports"></a>Odebrání nepotřebných použití/importů

**Odebrat nepotřebné použití/importy** rychlé akce `using` odebere všechny nepoužívané a `Import` direktivy pro aktuální soubor. Vyberete-li tuto položku, budou odebrány nepoužívané importy oborů názvů.

| Příslušné jazyky | Podporovaná verze |
| - | - |
| C# a Visual Basic | Visual Studio 2015 a novější |

### <a name="remove-unnecessary-cast"></a>Odebrání nepotřebného přetypátu

Pokud přetypování typu na jiný typ, který nevyžaduje přetypování, **odebrat zbytečné přetypování** rychlá akce položka odebere zbytečné přetypování.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# a Visual Basic | Visual Studio 2015 a novější |

### <a name="remove-unused-variables"></a>Odebrání nepoužívaných proměnných

Tato rychlá akce umožňuje odebrat proměnné, které byly deklarovány, ale nikdy použity ve vašem kódu.

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# a Visual Basic | Visual Studio 2017 verze 15.3 a novější |

### <a name="remove-type-from-default-value-expression"></a>Odebrat text z výrazu výchozí hodnoty

Tato rychlá akce odebere typ hodnoty z výchozího výrazu hodnoty a použije [výchozí literál,](/dotnet/csharp/language-reference/operators/default#default-literal) když kompilátor může odvodit typ výrazu.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1+ | Visual Studio 2017 verze 15.3 a novější |

## <a name="actions-that-add-missing-code"></a>Akce, které přidávají chybějící kód

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Přidání použití nebo importu pro typy v referenčních sestaveních, balíčcích NuGet nebo jiných typech v řešení

Pomocí typů umístěných v jiných projektech ve vašem řešení se automaticky zobrazí rychlá akce, ale ostatní musí být povoleny z **nástroje > možnosti > C#** nebo **základní > upřesnit** kartu:

- Navrhnout použití/importy pro typy v referenčních sestavách
- Navrhnout použití nebo importy pro typy v balíčcích NuGet

Pokud je povoleno, pokud použijete typ v oboru názvů, který není aktuálně importován, ale existuje v referenčním sestavení nebo balíčku NuGet, vytvoří se direktiva using nebo import.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

' After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

| ID diagnostiky | Příslušné jazyky |
| - | - |
| CS0103, BC30451 | C# a Visual Basic|

### <a name="add-missing-casesdefault-caseboth"></a>Přidání chybějících případů/výchozího případu/obojího

Při vytváření `switch` příkazu v `Select Case` jazyce C# nebo příkazu v jazyce Visual Basic můžete použít akci kódu k automatickému přidání chybějících položek případu, výchozího příkazu případu nebo obojího.

Zvažte následující výčet `switch` a `Select Case` prázdný nebo příkaz:

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

Použití **funkce Přidat obě** rychlé akce vyplní chybějící případy a přidá výchozí případ:

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# a Visual Basic| Visual Studio 2017 verze 15.3 a novější |

### <a name="add-null-checks-for-parameters"></a>Přidání nulových kontrol parametrů

Tato rychlá akce umožňuje přidat vrácení kódu se změnami, abyste zjistili, zda je parametr null.

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

| Příslušné jazyky | Podporovaná verze |
| -------------------- | ---------------- |
| C# a Visual Basic| Visual Studio 2017 verze 15.3 a novější |

### <a name="add-argument-name"></a>Přidání názvu argumentu

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

| Příslušné jazyky | Podporovaná verze |
| -------------------- | ---------------- |
| C# a Visual Basic| Visual Studio 2017 verze 15.3 a novější |

### <a name="add-braces"></a>Přidání závorek

Přidat složená závorky Rychlá akce `if` závorky kolem jednořádkové příkazy.

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true)
{
    return "hello,world";
}
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 a novější |

### <a name="add-and-order-modifiers"></a>Přidat a objednat modifikátory

Tyto rychlé akce pomáhají uspořádat modifikátory tím, že umožňují řadit existující a přidávat chybějící modifikátory usnadnění.

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```

```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# a Visual Basic| Visual Studio 2017 verze 15.5 a novější |
| IDE0040 | C# a Visual Basic| Visual Studio 2017 verze 15.5 a novější |

## <a name="code-transformations"></a>Transformace kódu

### <a name="convert-if-construct-to-switch"></a>Převést konstrukci if na přepínač

Tato rychlá akce umožňuje převést konstrukci **if-then-else** na konstrukci **přepínače.**

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

| Příslušné jazyky | Podporovaná verze |
| -------------------- | ---------------- |
| C# a Visual Basic| Visual Studio 2017 verze 15.3 a novější |

### <a name="convert-to-interpolated-string"></a>Převést na interpolovaný řetězec

[Interpolované řetězce](/dotnet/csharp/language-reference/keywords/interpolated-strings) jsou snadný způsob, jak vyjádřit řetězce s vloženými proměnnými, podobně jako **[string.Format](/dotnet/api/system.string.format#overloads)** metoda.  Tato rychlá akce rozpozná případy, kdy jsou řetězce zřetězené nebo pomocí **String.Format**, a změní použití na interpolovaný řetězec.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

| Příslušné jazyky | Podporovaná verze |
| -------------------- | ---------------- |
| C# 6.0+ a Visual Basic 14+ | Visual Studio 2017 a novější |

### <a name="use-object-initializers"></a>Použití inicializačních objektů

Tato rychlá akce umožňuje použít [inicializační metody objektu,](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) nikoli vyvolání konstruktoru a další řádky příkazů přiřazení.

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```

```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# a Visual Basic | Visual Studio 2017 a novější |

### <a name="use-collection-initializers"></a>Použít inicializátory kolekce

Tato rychlá akce umožňuje použít [inicializátory](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) `Add` kolekce spíše než více volání metody vaší třídy.

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```

```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# a Visual Basic | Visual Studio 2017 a novější |

### <a name="convert-auto-property-to-full-property"></a>Převést vlastnost auto na úplnou vlastnost

Tato rychlá akce umožňuje převést vlastnost auto na úplnou vlastnost a naopak.

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; }
}
```

```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property
```

| Příslušné jazyky | Podporovaná verze |
| -------------------- | ---------------- |
| C# a Visual Basic | Visual Studio 2017 verze 15.5 a novější |

### <a name="convert-block-body-to-expression-bodied-member"></a>Převést tělo bloku na člen s výrazem

Tato rychlá akce umožňuje převést těla bloků na členy s výrazem pro metody, konstruktory, operátory, vlastnosti, indexery a přistupující objekty.

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 a novější |

### <a name="convert-anonymous-function-to-local-function"></a>Převést anonymní funkci na místní funkci

Tato rychlá akce převádí anonymní funkce na místní funkce.

```csharp
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}
```

### <a name="convert-referenceequals-to-is-null"></a>Převést 'ReferenceEquals' na 'is null'

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0+ | Visual Studio 2017 verze 15.5 a novější |

Tato rychlá akce navrhuje použití [porovnávání](/dotnet/csharp/pattern-matching) ```ReferenceEquals``` vzorů spíše než kódovací vzor, kde je to možné.

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0+ | Visual Studio 2017 verze 15. a novější |

### <a name="introduce-pattern-matching"></a>Zavést porovnávání vzorů

Tato rychlá akce navrhuje použití [porovnávání vzorů](/dotnet/csharp/pattern-matching) s přetypování a null kontroly v jazyce C#.

```csharp
// Before
if (o is int)
{
    var i = (int)o;
    ...
}

// Use pattern matching

// After
if (o is int i)
{
    ...
}
```

```csharp
// Before
var s = o as string;
if (s != null)
{
    ...
}

// Use pattern matching

// After
if (o is string s)
{
    ...
}
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0020 | C# 7.0+ | Visual Studio 2017 a novější |
| IDE0019 | C# 7.0+ | Visual Studio 2017 a novější |

### <a name="change-base-for-numeric-literals"></a>Změnit základ pro číselné literály

Tato rychlá akce umožňuje převést číselný literál z jednoho základního číselného systému na jiný. Můžete například změnit číslo na šestnáctkové nebo na binární formát.

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```

```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

| Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| C# 7.0+ a Visual Basic 14+ | Visual Studio 2017 verze 15.3 a novější |

### <a name="insert-digit-separators-into-literals"></a>Vložení oddělovačů číslic do literál

Tato rychlá akce umožňuje přidat oddělovací znaky do literálových hodnot.

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```

```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

| Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| C# 7.0+ a Visual Basic 14+ | Visual Studio 2017 verze 15.3 a novější |

### <a name="use-explicit-tuple-names"></a>Použití explicitních názvů řazené kolekce členů

Tato rychlá akce identifikuje oblasti, kde lze použít explicitní názvy řazených členů, nikoli položky Item1, Item2 atd.

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```

```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0+ a Visual Basic 15+ | Visual Studio 2017 a novější |

### <a name="use-inferred-names"></a>Použití odvozených názvů

Tato rychlá akce poukazuje na to, kdy lze kód zjednodušit tak, aby se používaly odvozené názvy členů v anonymních typech nebo odvozené názvy prvků v řazených kolekcích a diáři.

```csharp
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```

```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | Visual Studio 2017 verze 15.5 a novější |
| IDE0037 | C# 7.1+ | Visual Studio 2017 verze 15.5 a novější |

### <a name="deconstruct-tuple-declaration"></a>Deconstruct n-tice prohlášení

Tato rychlá akce umožňuje deconstructing řazené kolekce členů proměnné deklarace.

```csharp
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

| ID diagnostiky | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0042 | C# 7.0+ | Visual Studio 2017 verze 15.5 a novější |

### <a name="make-method-synchronous"></a>Vytvořit metodu synchronní

Při použití `async` `Async` nebo klíčové slovo na metodu, očekává `await` se, že uvnitř této metody nebo `Await` klíčové slovo je také použit. Pokud tomu tak však není, zobrazí se rychlá akce, která způsobí `async` `Async` synchronní metodu odebráním klíčového slova nebo a změnou návratového typu. Použijte možnost **Vytvořit synchronní metodu** z nabídky Rychlé akce.

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

| ID chyby | Příslušné jazyky |
| ------- | -------------------- |
| CS1998, BC42356 | C# a Visual Basic |

### <a name="make-method-asynchronous"></a>Vytvořit metodu asynchronní

Při použití `await` `Await` nebo klíčové slovo uvnitř metody, očekává se, že `async` `Async` metoda je označena nebo klíčové slovo. Pokud tomu tak však není, zobrazí se rychlá akce, která způsobí, že metoda bude asynchronní. Použijte možnost **Vytvořit metodu/funkci asynchronní** z nabídky Rychlé akce.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

| ID chyby | Příslušné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| CS4032, BC37057 | C# a Visual Basic | Visual Studio 2017 a novější |

## <a name="see-also"></a>Viz také

- [Rychlé akce](../ide/quick-actions.md)
