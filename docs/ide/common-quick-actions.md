---
title: Běžné rychlé akce
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9c6eaa3b776e7a4c4e90795265f94af2d0df994b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894011"
---
# <a name="common-quick-actions"></a>Běžné rychlé akce

V oddílech v tomto tématu jsou uvedeny některé nejběžnější **rychlé akce** , která se dají použít pro kód jazyka C# i Visual Basic. Tyto akce jsou *opravy kódu* diagnostiky kompilátoru nebo předdefinované [analyzátory pro .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md) v sadě Visual Studio.

## <a name="actions-that-fix-errors"></a>Akce, které opravte chyby.

Rychlé akce v této části opravit chyby v kódu, která může způsobit selhání sestavení. Rychlé akce jsou dostupné a opravte chybu na řádku kódu, na ikonu, která se zobrazí na okraji nebo pod červená vlnovka se žárovka s red "x" v něm.

![Ikona chyby rychlé akce a nabídky](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Opravte chybně symbol nebo – klíčové slovo

Pokud budete mít překlep omylem typ nebo klíčové slovo v sadě Visual Studio, této rychlé akce ho automaticky opraví za vás. Uvidíte tyto položky v nabídce žárovky jako **"Změna"*chybně napsaná slova*"do"*opravit slovo*"**. Příklad:

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

| ID chyby | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| CS0103, BC30002 | C# a Visual Basic | Visual Studio 2015 Update 2 |

### <a name="resolve-git-merge-conflict"></a>Vyřešení konfliktu při slučování git

Tyto rychlé akce umožňují řešit konflikty sloučení git "přijímáním změnu", které odebere konfliktní kód a značky.

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

| ID chyby | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| CS8300, BC37284 | C# a Visual Basic | Visual Studio 2017 verze 15.3 |

## <a name="actions-that-remove-unnecessary-code"></a>Akce, které odeberte nepotřebný kód

### <a name="remove-unnecessary-usingsimports"></a>Odebrat nepotřebné direktivy using/importy

**Odebrat nepotřebné direktivy using/importy** rychlé akce odebere jakýkoli nesplněný `using` a `Import` příkazy pro aktuální soubor. Když vyberete tuto položku, se odeberou importů oboru názvu nevyužité.

| Použitelné jazyky | Podporovaná verze |
| -------------------- | ---------------- |
| C# a Visual Basic | Visual Studio 2015 RTW |

### <a name="remove-unnecessary-cast"></a>Odebrat nepotřebné přetypování

Pokud přetypování typu na jiný typ, který nevyžaduje přetypování, **odebrat nepotřebné přetypování** položky rychlé akce odebere nepotřebného přetypování.

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# a Visual Basic | Visual Studio 2015 RTW |

### <a name="remove-unused-variables"></a>Odebrat nepoužité proměnné

Tato rychlá akce umožňuje odebrat proměnné, které byly deklarovány, ale nikdy použit ve vašem kódu.

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# a Visual Basic | Visual Studio 2017 verze 15.3 |

### <a name="remove-type-from-default-value-expression"></a>Odebrání výchozí hodnota výrazu typu

Odebere typ hodnoty z výraz výchozí hodnoty této rychlé akce a používá [výchozí literál](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) Když kompilátor může odvodit typ výrazu.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1 + | Visual Studio 2017 verze 15.3 |

## <a name="actions-that-add-missing-code"></a>Akce, které aplikacím dodávají chybí kód

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Přidání direktivy using/importy pro typy v referenční sestavení, balíčky NuGet nebo jiných typů ve vašem řešení

Použití typů, které jsou umístěné v jiných projektech v rámci vašeho řešení se zobrazí rychlá akce automaticky, ale ostatní musí být povolené z **nástroje > Možnosti > C#** nebo **Základní > Upřesnit** kartu:

- Navrhnout použití/importy pro typy v sestaveních reference
- Navrhnout použití/importy pro typy v balíčcích NuGet

Pokud povolená, pokud použijete typ oboru názvů, který není v současnosti importovaná, ale existuje odkaz na sestavení nebo balíček NuGet, vytvoří se příkazu using nebo import.

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

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| CS0103, BC30451 | C# a Visual Basic| Visual Studio 2015 Update 2 |

### <a name="add-missing-casesdefault-caseboth"></a>Přidat chybějící případy/výchozí případ/jak

Při vytváření `switch` příkaz v jazyce C#, nebo `Select Case` příkaz v jazyce Visual Basic, vám pomůže akce kódu automaticky přidat chybějící případu položky, výchozí příkaz case nebo obojí.

Vezměte v úvahu následující výčet a prázdný `switch` nebo `Select Case` – příkaz:

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

Použití **přidejte** rychlá akce vyplní chybějící případy a přidá výchozí případ:

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# a Visual Basic| Visual Studio 2017 verze 15.3 |

### <a name="add-null-checks-for-parameters"></a>Přidat kontroly hodnot null pro parametry

Tato rychlá akce umožňuje přidat kontrolu v kódu zjistit, zda má parametr hodnotu null.

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

| Použitelné jazyky | Podporovaná verze |
| -------------------- | ---------------- |
| C# a Visual Basic| Visual Studio 2017 verze 15.3 |

### <a name="add-argument-name"></a>Přidat název argumentu

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

| Použitelné jazyky | Podporovaná verze |
| -------------------- | ---------------- |
| C# a Visual Basic| Visual Studio 2017 verze 15.3 |

### <a name="add-braces"></a>Přidat složené závorky

Přidat složené závorky rychlá akce zabalí složené závorky kolem jedním řádkem `if` příkazy.

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 RTW |

### <a name="add-and-order-modifiers"></a>Přidat a pořadí parametrů

Tyto rychlé akce lépe uspořádat modifikátory tím, že vám řazení existující a přidat chybějící modifikátory dostupnosti.

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# a Visual Basic| Visual Studio 2017 verze 15.5 |
| IDE0040 | C# a Visual Basic| Visual Studio 2017 verze 15.5 |

## <a name="code-transformations"></a>Transformace kódu

### <a name="convert-if-construct-to-switch"></a>Převést if konstrukce "přepínat.

Této rychlé akce umožňuje převést **if-then-else** vytvořit na **přepnout** vytvořit.

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

| Použitelné jazyky | Podporovaná verze |
| -------------------- | ---------------- |
| C# a Visual Basic| Visual Studio 2017 verze 15.3 |

### <a name="convert-to-interpolated-string"></a>Převést na interpolovaný řetězec

[Interpolované řetězce](/dotnet/csharp/language-reference/keywords/interpolated-strings) představují snadný způsob, jak vyjádřit řetězce pomocí vložených proměnných, podobně jako **[String.Format](/dotnet/api/system.string.format#overloads)** metody.  Tato rychlá akce rozpozná případech, kdy jsou řetězce zřetězených, nebo můžete použít **String.Format**a změní použití interpolovaného řetězce.

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

| Použitelné jazyky | Podporovaná verze |
| -------------------- | ---------------- |
| C# 6.0 + a Visual Basic 14 + | Visual Studio 2017 RTW |

### <a name="use-object-initializers"></a>Používejte inicializátory objektů

Tato rychlá akce umožňuje používat [inicializátorech objektu](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) namísto vyvoláním konstruktoru a s další řádky příkazů přiřazení.

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# a Visual Basic | Visual Studio 2017 RTW |

### <a name="use-collection-initializers"></a>Použijte inicializátory kolekce

Tato rychlá akce umožňuje používat [inicializátory kolekce](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) místo více volání `Add` metoda vaší třídy.

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# a Visual Basic | Visual Studio 2017 RTW |

### <a name="convert-auto-property-to-full-property"></a>Převést na celou vlastnost automatickou vlastnost

Této rychlé akce umožňuje automatickou vlastnost převést na celou vlastnost a naopak.

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

| Použitelné jazyky | Podporovaná verze |
| -------------------- | ---------------- |
| C# a Visual Basic | Visual Studio 2017 verze 15.5 |

### <a name="convert-block-body-to-expression-bodied-member"></a>Převést na s výrazem v těle členské text bloku

Tato rychlá akce umožňuje převést těla bloků s výrazem v těle členy pro metody, konstruktory, operátory, vlastnosti, indexery a přístupové objekty.

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0 + | Visual Studio 2017 RTW |

### <a name="convert-anonymous-function-to-local-function"></a>Převést anonymní funkci na místní funkce

Anonymní funkce této rychlé akce převede na místní funkce.

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

### <a name="convert-referenceequals-to-is-null"></a>Převést "ReferenceEquals" na "is null"

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0 + | Visual Studio 2017 verze 15.5 |

Navrhne použití této rychlé akce [porovnávání vzorů](/dotnet/csharp/pattern-matching) místo ```ReferenceEquals``` kódování – vzor, kde je to možné.

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0 + | Visual Studio 2017 verze 15.5 |

### <a name="introduce-pattern-matching"></a>Zavést porovnávání vzorů

Navrhne použití této rychlé akce [porovnávání vzorů](/dotnet/csharp/pattern-matching) pomocí přetypování a kontroly hodnoty null v jazyce C#.

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0020 | C# 7.0 + | Visual Studio 2017 RTW |
| IDE0019 | C# 7.0 + | Visual Studio 2017 RTW |

### <a name="change-base-for-numeric-literals"></a>Změnit základ pro číselné literály

Tato rychlá akce umožňuje převést číselný literál v jednom systému základní číselná. Můžete například změnit číslo do šestnáctkové nebo do binárního formátu.

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

| Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| C# 7.0 + a Visual Basic 14 + | Visual Studio 2017 verze 15.3 |

### <a name="insert-digit-separators-into-literals"></a>Oddělovače číslic: příkaz Insert literály

Tato rychlá akce umožňuje přidat oddělovací znaky do hodnoty literálu.

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

| Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| C# 7.0 + a Visual Basic 14 + | Visual Studio 2017 verze 15.3 |

### <a name="use-explicit-tuple-names"></a>Použít názvy explicitní řazené kolekce členů

Tato rychlá akce identifikuje oblasti, kde název explicitní řazené kolekce členů je možné místo Item1, item2 – atd.

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0 + a Visual Basic 15 + | Visual Studio 2017 RTW |

### <a name="use-inferred-names"></a>Použijte odvozené názvy

Tato rychlá akce poukazuje na, když kód se dá zjednodušit na použití odvozené názvy členů anonymních typů nebo odvozené názvy elementů v řazených kolekcí členů.

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | V aplikaci Visual Studio 2017. 15.5 |
| IDE0037 | C# 7.1 + | V aplikaci Visual Studio 2017. 15.5 |

### <a name="deconstruct-tuple-declaration"></a>Dekonstruovat deklaraci řazené kolekce členů

Tato rychlá akce umožní dekonstrukce deklarace proměnných řazené kolekce členů.

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

| ID diagnostiky | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| IDE0042 | C# 7.0 + | V aplikaci Visual Studio 2017. 15.5 |

### <a name="make-method-synchronous"></a>Nastavit metodu jako synchronní

Při použití `async` nebo `Async` – klíčové slovo pro metodu, očekává se, že, který v této metodě `await` nebo `Await` – klíčové slovo se také používá. Ale pokud to není tento případ, rychlá akce se zobrazí, která provádí synchronní metody tak, že odeberete `async` nebo `Async` – klíčové slovo a změnu návratového typu. Použití **nastavit metodu jako synchronní** možnost z nabídky rychlé akce.

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

| ID chyby | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| CS1998, BC42356 | C# a Visual Basic | Visual Studio 2015 Update 2 |

### <a name="make-method-asynchronous"></a>Provést asynchronní metody

Při použití `await` nebo `Await` – klíčové slovo v rámci metody, očekává se, že metoda je označena třídou `async` nebo `Async` – klíčové slovo. Ale pokud to není tento případ, rychlá akce se zobrazí, která provede asynchronní metodu. Použití **provést asynchronní metody/funkce** možnost z nabídky rychlé akce.

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

| ID chyby | Použitelné jazyky | Podporovaná verze |
| ------- | -------------------- | ---------------- |
| CS4032, BC37057 | C# a Visual Basic | Visual Studio 2017 |

## <a name="see-also"></a>Viz také:

- [Rychlé akce](../ide/quick-actions.md)
