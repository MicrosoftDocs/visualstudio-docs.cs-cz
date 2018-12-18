---
title: Nastavení pro EditorConfig konvence psaní kódu .NET
ms.date: 06/14/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: kuhlenh
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a54a3d6b967e7652c25e24922d7bd3b49141cc17
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769755"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>EditorConfig nastavení konvence psaní kódu .NET

V sadě Visual Studio 2017 můžete definovat a udržovat konzistentní kódu styl v vašeho základu kódu s použitím [EditorConfig](../ide/create-portable-custom-editor-options.md) souboru. EditorConfig obsahuje několik vlastností formátování core, jako například `indent_style` a `indent_size`. V sadě Visual Studio nastavení konvence psaní kódu .NET můžete také konfigurovat pomocí souboru EditorConfig. EditorConfig soubory umožňují povolit nebo zakázat jednotlivé konvence kódování .NET a nakonfigurovat míru, do kterého má být konvence vynucuje prostřednictvím úroveň závažnosti. Další informace o tom, jak můžete vynutit konzistenci ve vašem základu kódu EditorConfig, [vytvoření přenosné vlastní editor možnosti](../ide/create-portable-custom-editor-options.md).

Najdete na konci tohoto článku [souboru .editorconfig příklad](#example-editorconfig-file).

## <a name="convention-categories"></a>Vytváření kategorie

Existují tři podporované .NET kódování konvence kategorie:

- [Styly kódu jazyka](#language-code-styles)

   Pravidla týkající se jazyka C# nebo Visual Basic. Například můžete zadat pravidla ohledně použití `var` nebo explicitních typů, při definování proměnných nebo preferují s výrazem v těle členy.

- [Konvence formátování](#formatting-conventions)

   Pravidla týkající se rozložení a struktura vašeho kódu, aby bylo možné snadněji čitelné. Například můžete zadat pravidla ohledně Allman složené závorky nebo preferují mezery v řídicí bloky.

- [Zásady vytváření názvů](../ide/editorconfig-naming-conventions.md)

   Pravidla týkající se názvů prvků kódu. Například můžete určit, že `async` musí metod končí slovem "Async".

## <a name="language-code-styles"></a>Styly kódu jazyka

Pravidla pro jazyk kódu stylů mít následující formát:

`options_name = false|true : none|silent|suggestion|warning|error`

Pro každé pravidlo stylu kódu jazyka, musíte zadat buď **true** (preferovat tímto stylem) nebo **false** (nepreferovat tímto stylem) a **závažnost**. Závažnost určuje úroveň výkonu pro tento styl.

Následující tabulka uvádí možné závažnost hodnoty a jejich důsledky:

Závažnost | Efekt
:------- | ------
`none` | Nezobrazovat nic uživateli při porušení tohoto pravidla. Funkce generování kódu ale generování kódu v tomto stylu. Pravidla s `none` závažnost nikdy objeví v **rychlé akce a Refaktoringy** nabídky. Ve většině případů to považován za "zakázáno" nebo "ignoruje".
`silent` (také `refactoring` v sadě Visual Studio 2017 verze 15.8) | Nezobrazovat nic uživateli při porušení tohoto pravidla. Funkce generování kódu ale generování kódu v tomto stylu. Pravidla s `silent` závažnost účastnit vyčištění stejně jako se zobrazí v **rychlé akce a Refaktoringy** nabídky.
`suggestion` | Při porušení tohoto pravidla stylu, zobrazí se uživateli jako návrh. Návrhy jeví jako tři šedé tečky v prvních dvou znacích.
`warning` | Při porušení tohoto pravidla stylu zobrazení upozornění kompilátoru.
`error` | Při porušení tohoto pravidla stylu, zobrazit chybu kompilátoru.

Následující seznam uvádí jazyka povolená nastavení stylu kódu:

- Nastavení stylu kódu .NET
    - ["This." a "Me." kvalifikátory](#this_and_me)
        - DotNet\_styl\_kvalifikace\_for_field
        - dotnet\_style\_qualification\_for_property
        - DotNet\_styl\_kvalifikace\_for_method
        - DotNet\_styl\_kvalifikace\_for_event
    - [Klíčová slova jazyka místo framework názvy typů pro odkazy na typ](#language_keywords)
        - DotNet\_styl\_předdefinované\_typ\_pro\_lokální\_parameters_members
        - DotNet\_styl\_předdefinované\_typ\_pro\_member_access
    - [Modifikátor předvolby](#normalize_modifiers)
        - DotNet\_styl\_vyžadují\_accessibility_modifiers
        - csharp\_preferred\_modifier_order
        - visual\_basic\_preferred\_modifier_order
        - DotNet\_styl\_jen pro čtení\_pole
    - [Předvolby závorky](#parentheses)
        - DotNet\_styl\_závorky\_v\_aritmetické\_binární\_operátory
        - DotNet\_styl\_závorky\_v\_jiných\_binární\_operátory
        - DotNet\_styl\_závorky\_v\_jiných\_operátory
        - DotNet\_styl\_závorky\_v\_relační\_binární\_operátory
    - [Předvolby výrazu úrovni](#expression_level)
        - DotNet\_styl\_object_initializer
        - DotNet\_styl\_collection_initializer
        - DotNet\_styl\_explicitní\_tuple_names
        - DotNet\_styl\_raději\_odvodit\_tuple_names
        - DotNet\_styl\_raději\_odvodit\_anonymní\_typ\_member_names
        - DotNet\_styl\_raději\_automaticky\_vlastnosti
        - DotNet\_styl\_raději\_je\_null\_zkontrolujte\_přes\_odkaz\_rovnosti\_– metoda
        - DotNet\_styl\_raději\_podmíněného\_výraz\_přes\_přiřazení
        - DotNet\_styl\_raději\_podmíněného\_výraz\_přes\_vrátit
    - ["Null" Kontrola předvolby](#null_checking)
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
- Nastavení stylu kódu C#
    - [Implicitní a explicitní typy](#implicit-and-explicit-types)
        - CSharp\_styl\_var\_pro\_vytvořené\_in_types
        - CSharp\_styl\_var\_při\_typ\_is_apparent
        - csharp\_style\_var_elsewhere
    - [Členové tvoření výrazy](#expression_bodied_members)
        - CSharp\_styl\_výraz\_bodied_methods
        - csharp\_style\_expression\_bodied_constructors
        - csharp\_style\_expression\_bodied_operators
        - csharp\_style\_expression\_bodied_properties
        - csharp\_style\_expression\_bodied_indexers
        - csharp\_style\_expression\_bodied_accessors
    - [Porovnávání vzorů](#pattern_matching)
        - CSharp\_styl\_vzor\_odpovídající\_přes\_je\_s\_cast_check
        - CSharp\_styl\_vzor\_odpovídající\_přes\_jako\_s\_null_check
    - [Vložená deklarace proměnné](#inlined_variable_declarations)
        - CSharp\_styl\_vložených\_variable_declaration
    - [Předvolby výrazu úrovni](#expression_level_csharp)
        - csharp\_prefer\_simple\_default_expression
        - CSharp\_styl\_dekonstruovat\_variable_declaration
        - CSharp\_styl\_vzor\_místní\_přes\_anonymous_function
    - ["Null" Kontrola předvolby](#null_checking_csharp)
        - csharp\_style\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [Předvolby bloku kódu](#code_block)
        - csharp\_prefer_braces

### <a name="net-code-style-settings"></a>Nastavení stylu kódu .NET

Pravidla stylu v této části se vztahují na C# i Visual Basic. Chcete-li zobrazit příklady kódu ve vašem preferovaném programovacím jazyce, zvolte v rozevíracím seznamu **jazyk** nabídky v pravém horním rohu okna prohlížeče.

#### <a name="this_and_me"></a>"This." a "Me." Kvalifikátory

Toto pravidlo stylu (pravidlo IDE0003 ID a IDE0009) můžete použít pro pole, vlastnosti, metody nebo události. Hodnota **true** znamená, že raději symbol kódu, chcete-li být uvozena řetězcem `this.` v jazyce C# nebo `Me.` v jazyce Visual Basic. Hodnota **false** znamená, že raději prvek kódu _není_ Chcete-li být uvozena řetězcem `this.` nebo `Me.`.

Následující tabulka uvádí názvy pravidel, použitelné programovací jazyky a výchozí hodnoty:

| Název pravidla | Použitelné jazyky | Visual Studio výchozí hodnotu |
| ----------- | -------------------- | ----------------------|
| dotnet_style_qualification_for_field | C# a Visual Basic | FALSE: žádné |
| dotnet_style_qualification_for_property | C# a Visual Basic | FALSE: žádné |
| dotnet_style_qualification_for_method | C# a Visual Basic | FALSE: žádné |
| dotnet_style_qualification_for_event | C# a Visual Basic | FALSE: žádné |

**DotNet\_styl\_kvalifikace\_for_field**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost pole být uvozena řetězcem `this.` v jazyce C# nebo `Me.` v jazyce Visual Basic.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost pole _není_ Chcete-li být uvozena řetězcem `this.` nebo `Me.`.

Příklady kódu:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

**dotnet\_style\_qualification\_for_property**

- Pokud toto pravidlo je nastaven na **true**, preferovat vlastnosti, které chcete být uvozena řetězcem `this.` v jazyce C# nebo `Me.` v jazyce Visual Basic.
- Pokud toto pravidlo je nastaven na **false**, preferovat vlastnosti _není_ Chcete-li být uvozena řetězcem `this.` nebo `Me.`.

Příklady kódu:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

**DotNet\_styl\_kvalifikace\_for_method**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost metody být uvozena řetězcem `this.` v jazyce C# nebo `Me.` v jazyce Visual Basic.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost metody _není_ Chcete-li být uvozena řetězcem `this.` nebo `Me.`.

Příklady kódu:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

**DotNet\_styl\_kvalifikace\_for_event**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost události, které mají být uvozena řetězcem `this.` v jazyce C# nebo `Me.` v jazyce Visual Basic.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost události _není_ Chcete-li být uvozena řetězcem `this.` nebo `Me.`.

Příklady kódu:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

Tato pravidla mohou být zobrazeny v *.editorconfig* to následujícím způsobem:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords"></a>Klíčová slova jazyka místo framework názvy typů pro odkazy na typ

Do místní proměnné, parametry metody a členy třídy, nebo jako samostatné pravidlo zadejte výrazy členského přístupu může být použito toto pravidlo stylu. Hodnota **true** znamená, že raději klíčové slovo jazyka (například `int` nebo `Integer`) namísto názvu typu (například `Int32`) pro typy, které mají klíčové slovo představující je. Hodnota **false** raději znamená, že název typu místo klíčového slova jazyka.

V následující tabulce jsou uvedeny názvy pravidel, pravidel ID, použitelné programovací jazyky a výchozí hodnoty:

| Název pravidla | ID pravidla | Použitelné jazyky | Visual Studio výchozí |
| --------- | ------- | -------------------- | ----------------------|
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 a IDE0014 | C# a Visual Basic | true: žádné |
| dotnet_style_predefined_type_for_member_access | IDE0013 a IDE0015 | C# a Visual Basic | true: žádné |

**DotNet\_styl\_předdefinované\_typ\_pro\_lokální\_parameters_members**

- Pokud toto pravidlo je nastaven na **true**, raději klíčové slovo jazyka pro místní proměnné, parametry metody a třídy členy, namísto názvu typu, pro typy, které mají klíčové slovo představující je.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost název typu pro místní proměnné, parametry metody a třídy členy, místo klíčového slova jazyka.

Příklady kódu:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

**DotNet\_styl\_předdefinované\_typ\_pro\_member_access**

- Pokud toto pravidlo je nastaven na **true**, raději klíčové slovo jazyka pro výrazy přístupu členů, namísto názvu typu, pro typy, které mají klíčové slovo představující je.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost název typu pro výrazy přístupu členů, místo klíčového slova jazyka.

Příklady kódu:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

Tato pravidla mohou být zobrazeny v *.editorconfig* to následujícím způsobem:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="normalize_modifiers"></a>Modifikátor předvolby

Pravidla stylu v této části se týkají modifikátor předvolby, včetně vyžadování modifikátory, zadávat pořadí řazení požadované modifikátor která vyžaduje modifikátor jen pro čtení.

V následující tabulce jsou uvedeny názvy pravidel, pravidel ID, použitelné programovací jazyky, výchozí hodnoty a první podporovanou verzi sady Visual Studio:

| Název pravidla | ID pravidla | Použitelné jazyky | Visual Studio výchozí | Visual Studio 2017 verze |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| dotnet_style_require_accessibility_modifiers | IDE0040 | C# a Visual Basic | for_non_interface_members:none | 15.5 |
| csharp_preferred_modifier_order | IDE0036 | C# | veřejné, privátní, chráněné, interní, static a extern, nový, virtuální, abstraktní, zapečetěné, přepsání, jen pro čtení, nebezpečný, ale volatilních, asynchronní: žádné | 15.5 |
| visual_basic_preferred_modifier_order | IDE0036 | Visual Basic | Částečné výchozí, privátní, chráněné veřejné, Friend, NotOverridable, Overridable, MustOverride, přetížení, přepsání, MustInherit, NotInheritable, statická, sdílí, Shadows, ReadOnly, jen pro zápis, dimenze, Const, WithEvents, rozšíření, zužující, vlastní, Asynchronní: žádné | 15.5 |
| dotnet_style_readonly_field | IDE0044 | C# a Visual Basic | true: návrh | verzi 15.7 |

**DotNet\_styl\_vyžadují\_accessibility_modifiers**

Toto pravidlo nepřijímá **true** nebo **false** hodnota; místo toho přijímá hodnotu z následující tabulky:

| Hodnota | Popis |
| ----- |:----------- |
| Vždy | Modifikátory dostupnosti. Chcete-li zadat raději |
| pro\_bez\_interface_members | Preferovat modifikátory deklarovat s výjimkou veřejné členy. To je stejný jako **vždy** a byla přidána pro budoucí kontroly pravopisu, pokud C# přidá výchozí metody rozhraní. |
| Nikdy | Nepreferovat modifikátory zadání |

Příklady kódu:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

**csharp_preferred_modifier_order**

- Pokud toto pravidlo je nastaven na seznam parametrů, dáváte přednost zadaného pořadí.
- Pokud toto pravidlo je vynechán ze souboru, nepreferovat modifikátor pořadí.

Příklady kódu:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

**visual_basic_preferred_modifier_order**

- Pokud toto pravidlo je nastaven na seznam parametrů, dáváte přednost zadaného pořadí.
- Pokud toto pravidlo je vynechán ze souboru, nepreferovat modifikátor pořadí.

Příklady kódu:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

**dotnet_style_readonly_field**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost, že pole by měly být označené `readonly` (C#) nebo `ReadOnly` (Visual Basic) Pokud jsou pouze přiřazeno vložené, nebo v konstruktoru.
- Pokud toto pravidlo je nastaven na **false**, zadejte žádná předvolba přes Určuje, zda by měly být označené pole `readonly` (C#) nebo `ReadOnly` (Visual Basic).

Příklady kódu:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

Tato pravidla mohou být zobrazeny v *.editorconfig* to následujícím způsobem:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="parentheses"></a>Předvolby závorky

Pravidla stylu v této části se týkají předvolby závorky, včetně použití závorek pro aritmetické, relační a ostatní binární operátory.

V následující tabulce jsou uvedeny názvy pravidel, pravidel ID, použitelné programovací jazyky, výchozí hodnoty a první podporovanou verzi sady Visual Studio:

| Název pravidla | ID pravidla | Použitelné jazyky | Visual Studio výchozí | Visual Studio 2017 verze |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_parentheses_in_arithmetic_binary_operators | IDE0047 | C# a Visual Basic | always_for_clarity: žádné | 15.8 |
| dotnet_style_parentheses_in_relational_binary_operators | IDE0047 | C# a Visual Basic | always_for_clarity: žádné | 15.8 |
| dotnet_style_parentheses_in_other_binary_operators | IDE0047 | C# a Visual Basic | always_for_clarity: žádné | 15.8 |
| dotnet_style_parentheses_in_other_operators | IDE0047 | C# a Visual Basic | never_if_unnecessary: žádné | 15.8 |

**DotNet\_styl\_závorky\_v\_aritmetické\_binary_operators**

- Pokud toto pravidlo je nastaven na **always_for_clarity**, dáváte přednost závorky pro upřesnění aritmetického operátoru (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) prioritu.
- Pokud toto pravidlo je nastaven na **never_if_unnecessary**, nepřejete závorky, pokud aritmetického operátoru (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) priorita je zřejmý.

Příklady kódu:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

**DotNet\_styl\_závorky\_v\_relační\_binary_operators**

- Pokud toto pravidlo je nastaven na **always_for_clarity**, dáváte přednost závorky pro upřesnění relační operátor (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) prioritu.
- Pokud toto pravidlo je nastaven na **never_if_unnecessary**, nepřejete závorky, pokud relační operátor (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) priorita je zřejmý.

Příklady kódu:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

**DotNet\_styl\_závorky\_v\_jiných\_binary_operators**

- Pokud toto pravidlo je nastaven na **always_for_clarity**, dáváte přednost závorky pro upřesnění ostatních binárních operátorů (`&&`, `||`, `??`) prioritu.
- Pokud toto pravidlo je nastaven na **never_if_unnecessary**, nepřejete závorky po ostatních binárních operátorů (`&&`, `||`, `??`) priorita je zřejmý.

Příklady kódu:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

**DotNet\_styl\_závorky\_v\_other_operators**

- Pokud toto pravidlo je nastaven na **always_for_clarity**, dáváte přednost závorky pro upřesnění priorita operátorů.
- Pokud toto pravidlo je nastaven na **never_if_unnecessary**, nepřejete závorky po zřejmé priorita operátorů.

Příklady kódu:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

Tato pravidla mohou být zobrazeny v *.editorconfig* to následujícím způsobem:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:none
```

#### <a name="expression_level"></a>Předvolby výrazu úrovni

Styl pravidla v této části problém úrovni výrazu předvolby včetně využití čipu TPM inicializátory objektů, inicializátory kolekce, názvy explicitní nebo odvozený řazené kolekce členů a odvodit anonymních typů.

V následující tabulce jsou uvedeny názvy pravidel, pravidel ID, použitelné programovací jazyky, výchozí hodnoty a první podporovanou verzi sady Visual Studio:

| Název pravidla | ID pravidla | Použitelné jazyky | Visual Studio výchozí | Visual Studio 2017 verze |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_object_initializer | IDE0017 | C# a Visual Basic | true: návrh | První verze |
| dotnet_style_collection_initializer | IDE0028 | C# a Visual Basic | true: návrh | První verze |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0 + a Visual Basic 15 + | true: návrh | První verze |
| dotnet_style_prefer_inferred_tuple_names | IDE0037 | C# 7.1 + a Visual Basic 15 + | true: návrh | verzi 15.6 |
| dotnet_style_prefer_inferred_anonymous_type_member_names | IDE0037 | C# a Visual Basic | true: návrh | verzi 15.6 |
| dotnet_style_prefer_auto_properties | IDE0032 | C# a Visual Basic | true: žádné | verzi 15.7 |
| dotnet_style_prefer_is_null_check_over_reference_equality_method | IDE0041 | C# a Visual Basic | true: návrh | verzi 15.7 |
| dotnet_style_prefer_conditional_expression_over_assignment | IDE0045 | C# a Visual Basic | true: žádné | 15.8 |
| dotnet_style_prefer_conditional_expression_over_return | IDE0046 | C# a Visual Basic | true: žádné | 15.8 |

**DotNet\_styl\_object_initializer**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost objekty inicializovat inicializátory objektů, pokud je to možné.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost objektů *není* být inicializován pomocí inicializátory objektů.

Příklady kódu:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

**DotNet\_styl\_collection_initializer**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost kolekcí, které mají být inicializovány pomocí inicializátory kolekce, pokud je to možné.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost kolekcí *není* být inicializován pomocí inicializátory kolekce.

Příklady kódu:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

**DotNet\_styl\_explicitní\_tuple_names**

- Pokud toto pravidlo je nastaven na **true**, raději ItemX vlastnosti názvy řazené kolekce členů.
- Pokud toto pravidlo je nastaven na **false**, raději ItemX vlastnosti názvy řazené kolekce členů.

Příklady kódu:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

**DotNet\_styl\_raději\_odvodit\_tuple_names**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost názvy elementů řazené kolekce členů odvozený.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost názvy elementů řazené kolekce členů explicitní.

Příklady kódu:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

**DotNet\_styl\_raději\_odvodit\_anonymní\_typ\_member_names**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost názvy členů anonymního typu.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost názvy členů anonymních typů explicitní.

Příklady kódu:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

**DotNet\_styl\_raději\_automaticky\_vlastnosti**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost autoproperties prostřednictvím vlastností s privátní pomocné pole.
- Pokud toto pravidlo je nastaven na **false**, přes autoproperties preferovat vlastnosti s privátní pomocné pole.

Příklady kódu:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

**DotNet\_styl\_raději\_je\_null\_zkontrolujte\_přes\_odkaz\_rovnosti\_– metoda**

- Pokud toto pravidlo je nastaven na **true**, přednost používání kontrolu hodnot null pomocí porovnávání vzorů přes objekt. ReferenceEquals.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost objektu. ReferenceEquals přes kontrolu hodnot null s porovnáváním vzorů.

Příklady kódu:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```



**DotNet\_styl\_raději\_podmíněného\_výraz\_over_assignment**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost přiřazení s Ternární podmíněné přes if-else – příkaz.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost přiřazení s if-else – příkaz přes Ternární podmíněné.

Příklady kódu:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

**DotNet\_styl\_raději\_podmíněného\_výraz\_over_return**

- Pokud toto pravidlo je nastaven na **true**, raději příkazy na používání Ternární podmíněné přes if-else – příkaz return.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost návratovými příkazy na používání přes Ternární podmínka if-else – příkaz.

Příklady kódu:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

Tato pravidla mohou být zobrazeny v *.editorconfig* to následujícím způsobem:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:none
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
```

#### <a name="null_checking"></a>Předvolby kontrol Null

Pravidla stylu v této části se týkají předvolby kontrol null.

V následující tabulce jsou uvedeny názvy pravidel, pravidel ID, použitelné programovací jazyky, výchozí hodnoty a první podporovanou verzi sady Visual Studio:

| Název pravidla | ID pravidla | Použitelné jazyky | Visual Studio výchozí | Visual Studio 2017 verze |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_coalesce_expression | IDE0029 | C# a Visual Basic | true: návrh | První verze |
| dotnet_style_null_propagation | IDE0031 | C# 6.0 + a Visual Basic 14 + | true: návrh | První verze |

**dotnet\_style\_coalesce_expression**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost null slučovací výrazy Ternární operátor kontrolu.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost tříhodnotový operátor kontrola null slučovací výrazy.

Příklady kódu:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

**dotnet\_style\_null_propagation**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost operátor podmíněných null, pokud je to možné.
- Pokud toto pravidlo je nastaven na **false**, dávají přednost používání Ternární kontroluje hodnotu null, kde je to možné.

Příklady kódu:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

Tato pravidla mohou být zobrazeny v *.editorconfig* to následujícím způsobem:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

### <a name="c-code-style-settings"></a>Nastavení stylu kódu C#

Pravidla stylu v této části jsou pouze pro C#.

#### <a name="implicit-and-explicit-types"></a>Implicitní a explicitní typy

Pravidla stylu v této části (pravidlo IDE0007 ID a IDE0008) se týkají používání [var](/dotnet/csharp/language-reference/keywords/var) – klíčové slovo oproti explicitního typu v deklaraci proměnné. Toto pravidlo můžete použít samostatně předdefinovaných typů, když typ je zřejmý a jinde.

Následující tabulka uvádí názvy pravidel, použitelné programovací jazyky a výchozí hodnoty:

| Název pravidla | Použitelné jazyky | Visual Studio výchozí |
| ----------- | -------------------- | ----------------------|
| csharp_style_var_for_built_in_types | C# | true: žádné |
| csharp_style_var_when_type_is_apparent | C# | true: žádné |
| csharp_style_var_elsewhere | C# | true: žádné |

**CSharp\_styl\_var\_pro\_vytvořené\_in_types**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost `var` se používá k deklaraci proměnné s typy integrovaných systémů, jako `int`.
- Pokud toto pravidlo je nastaven na **false**, preferovat explicitní typ přes `var` k deklaraci proměnné s typy integrovaných systémů, jako `int`.

Příklady kódu:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**csharp\_style\_var\_when\_type\_is_apparent**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost `var` když typ již uvedeno na pravé straně deklarace výrazu.
- Pokud toto pravidlo je nastaven na **false**, preferovat explicitní typ přes `var` když typ již uvedeno na pravé straně deklarace výrazu.

Příklady kódu:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost `var` přes explicitního typu ve všech případech, pokud není přepsán jiným pravidlem styl kódu.
- Pokud toto pravidlo je nastaven na **false**, preferovat explicitní typ přes `var` ve všech případech, pokud není přepsán jiným pravidlem styl kódu.

Příklady kódu:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

Příklad *.editorconfig* souboru:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="expression_bodied_members"></a>Členové tvoření výrazy

Pravidla stylu v této části se týkají používání [členové tvoření](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) při logika se skládá z jediného výrazu. Toto pravidlo lze použít pro metody, konstruktory, operátory, vlastnosti, indexery a přístupové objekty.

V následující tabulce jsou uvedeny názvy pravidel, pravidel ID, příslušné jazykové verze, výchozí hodnoty a první podporovanou verzi sady Visual Studio:

| Název pravidla | ID pravidla | Použitelné jazyky | Visual Studio výchozí | Visual Studio 2017 verze |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0 + | FALSE: žádné | 15.3 |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0 + | FALSE: žádné | 15.3 |
| csharp_style_expression_bodied_operators | IDE0023 a IDE0024 | C# 7.0 + | FALSE: žádné | 15.3 |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0 + | true: žádné | 15.3 |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0 + | true: žádné | 15.3 |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0 + | true: žádné | 15.3 |

**csharp\_style\_expression\_bodied_methods**

Toto pravidlo je možné zadat hodnoty v následující tabulce:

| Hodnota | Popis |
| ----- |:----------- |
| true | Preferovat členy s výrazem v těle metody |
| when_on_single_line | Preferovat členy s výrazem v těle metody, když bude se jednat o jeden řádek |
| false | Preferovat těla bloků pro metody |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

**csharp\_style\_expression\_bodied_constructors**

Toto pravidlo je možné zadat hodnoty v následující tabulce:

| Hodnota | Popis |
| ----- |:----------- |
| true | Preferovat členové tvoření konstruktorů |
| when_on_single_line | Dáváte přednost členové tvoření pro konstruktory, když bude se jednat o jeden řádek |
| false | Preferovat těla bloků pro konstruktory |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

**csharp\_style\_expression\_bodied_operators**

Toto pravidlo je možné zadat hodnoty v následující tabulce:

| Hodnota | Popis |
| ----- |:----------- |
| true | Preferovat členové tvoření pro operátory |
| when_on_single_line | Preferovat členové tvoření pro operátory, když bude se jednat o jeden řádek |
| false | Preferovat těla bloků pro operátory |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

**csharp\_style\_expression\_bodied_properties**

Toto pravidlo je možné zadat hodnoty v následující tabulce:

| Hodnota | Popis |
| ----- |:----------- |
| true | Preferovat s výrazem v těle členy pro vlastnosti |
| when_on_single_line | Raději s výrazem v těle členy pro vlastnosti, když bude se jednat o jeden řádek |
| false | Preferovat těla bloků pro vlastnosti |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

**csharp\_style\_expression\_bodied_indexers**

Toto pravidlo je možné zadat hodnoty v následující tabulce:

| Hodnota | Popis |
| ----- |:----------- |
| true | Preferovat členové tvoření pro indexery |
| when_on_single_line | Členové tvoření pro indexery dáváte přednost, když bude se jednat o jeden řádek |
| false | Preferovat těla bloků pro indexery |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

**csharp\_style\_expression\_bodied_accessors**

Toto pravidlo je možné zadat hodnoty v následující tabulce:

| Hodnota | Popis |
| ----- |:----------- |
| true | Preferovat s výrazem v těle členy pro přístupové objekty |
| when_on_single_line | Členové tvoření pro přistupující objekty dáváte přednost, když bude se jednat o jeden řádek |
| false | Preferovat těla bloků pro přístupové objekty |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

Příklad *.editorconfig* souboru:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="pattern_matching"></a>Porovnávání vzorů

Pravidla stylu v této části se týkají používání [porovnávání vzorů](/dotnet/csharp/pattern-matching) v jazyce C#.

V následující tabulce jsou uvedeny pravidlo názvy, ID pravidel, příslušné jazykové verze a výchozí hodnoty:

| Název pravidla | ID pravidla | Použitelné jazyky | Visual Studio výchozí |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0 + | true: návrh |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0 + | true: návrh |

**CSharp\_styl\_vzor\_odpovídající\_přes\_je\_s\_cast_check**

- Pokud toto pravidlo je nastaven na **true**, preferovat porovnávání vzorů místo `is` výrazy s přetypování.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost `is` výrazy s přetypování namísto porovnávání vzorů.

Příklady kódu:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**

- Pokud toto pravidlo je nastaven na **true**, preferovat porovnávání vzorů místo `as` výrazy s kontroly hodnoty null pro určení, zda je něco určitého typu.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost `as` výrazy s kontroly hodnoty null namísto porovnávání vzorů pro určení, zda je něco určitého typu.

Příklady kódu:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

Příklad *.editorconfig* souboru:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations"></a>Vložená deklarace proměnné

Tento styl, jestli pravidlo se týká `out` proměnné jsou deklarovaná jako inline nebo ne. Spuštění v jazyce C# 7, můžete [deklarovat proměnnou nejsou v seznamu argumentů volání metody](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), nikoli v samostatné deklarace proměnné.

V následující tabulce jsou uvedeny název pravidla, ID pravidla, příslušné jazykové verze a výchozí hodnoty:

| Název pravidla | ID pravidla | Použitelné jazyky | Visual Studio výchozí |
| --------- | -------- | -------------------- | ----------------------|
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0 + | true: návrh |

**CSharp\_styl\_vložených\_variable_declaration**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost `out` proměnné se nedá deklarovat vloženě v seznamu argumentů volání metody, pokud je to možné.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost `out` proměnné deklarované před voláním metody.

Příklady kódu:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Příklad *.editorconfig* souboru:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp"></a>Předvolby výrazu úrovni

Pravidla stylu v této části se týkají předvolby výrazu úrovni, včetně použití [výchozí výrazy](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), dekonstruovanou proměnné a lokální funkce přes anonymní funkce.

V následující tabulce jsou uvedeny název pravidla, ID pravidla, příslušné jazykové verze, výchozí hodnoty a první podporovanou verzi sady Visual Studio:

| Název pravidla | ID pravidla | Použitelné jazyky | Visual Studio výchozí | Visual Studio 2017 verze |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1 + | true: návrh | 15.3 |
| csharp_style_deconstructed_variable_declaration | IDE0042 | C# 7.0 + | true: návrh | 15.5 |
| csharp_style_pattern_local_over_anonymous_function | IDE0039 | C# 7.0 + | true: návrh | 15.5 |

**csharp\_prefer\_simple\_default_expression**

Toto pravidlo stylu se týká použití [ `default` literál pro výrazy s výchozími hodnotami](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) Když kompilátor může odvodit typ výrazu.

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost `default` přes `default(T)`.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost `default(T)` přes `default`.

Příklady kódu:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

**CSharp\_styl\_dekonstruovat\_variable_declaration**

- Pokud toto pravidlo je nastaven na **true**, upřednostňovat dekonstruovanou deklaraci proměnných.
- Pokud toto pravidlo je nastaven na **false**, nepreferovat dekonstrukce v deklaracích proměnných.

Příklady kódu:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

**CSharp\_styl\_vzor\_místní\_přes\_anonymous_function**

- Pokud toto pravidlo je nastaven na **true**, dáváte přednost lokální funkce přes anonymní funkce.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost anonymní funkce přes lokální funkce.

Příklady kódu:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

Příklad *.editorconfig* souboru:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="null_checking_csharp"></a>"Null" Kontrola předvolby

Tyto obavy pravidla stylu syntaxe kolem `null` kontrolu, včetně použití `throw` výrazy nebo `throw` příkazy a zda chcete provést kontrolu hodnot null, nebo použít podmíněný operátor sloučení (`?.`) při vyvolání [výraz lambda](/dotnet/csharp/lambda-expressions).

V následující tabulce jsou uvedeny pravidlo názvy, ID pravidel, příslušné jazykové verze a výchozí hodnoty:

| Název pravidla | ID pravidla | Použitelné jazyky | Visual Studio výchozí |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_throw_expression | IDE0016 | C# 7.0 + | true: návrh |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0 + | true: návrh |

**csharp\_style\_throw_expression**

- Pokud toto pravidlo je nastaven na **true**, dávají přednost používání `throw` výrazy místo `throw` příkazy.
- Pokud toto pravidlo je nastaven na **false**, dávají přednost používání `throw` příkazy místo `throw` výrazy.

Příklady kódu:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**

- Pokud toto pravidlo je nastaven na **true**, dávají přednost používání podmíněný operátor sloučení (`?.`) při vyvolání lambda výraz, takže nemusíte provádět s hodnotou null zkontrolovat.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost provádět kontrolu hodnot null před vyvoláním lambda výrazu, namísto použití podmíněný operátor sloučení (`?.`).

Příklady kódu:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

Příklad *.editorconfig* souboru:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block"></a>Předvolby bloku kódu

Toto pravidlo stylu se týká použití složené závorky `{ }` ohraničit bloky kódu.

V následující tabulce jsou uvedeny název pravidla, ID pravidla, příslušné jazykové verze, výchozí hodnoty a první podporovanou verzi sady Visual Studio:

| Název pravidla | ID pravidla | Použitelné jazyky | Visual Studio výchozí | Visual Studio 2017 verze |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_braces | IDE0011 | C# | true: žádné | 15.3 |

**csharp\_prefer\_braces**

- Pokud toto pravidlo je nastaven na **true**, preferovat složené závorky i pro jeden řádek kódu.
- Pokud toto pravidlo je nastaven na **false**, dáváte přednost žádné složené závorky, pokud může.

Příklady kódu:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

Příklad *.editorconfig* souboru:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

## <a name="formatting-conventions"></a>Konvence formátování

Většina pravidel pro konvence formátování má následující formát:

`rule_name = false|true`

Zadejte buď **true** (preferovat tímto stylem) nebo **false** (nepreferovat tímto stylem). Závažnost není zadán. Několik pravidel, namísto hodnotu true nebo false zadat jiné hodnoty k popisu, kdy a kde použít pravidlo.

Následující seznam ukazuje dostupné v sadě Visual Studio pravidla formátování konvence:

- Nastavení formátování rozhraní .NET
    - [Uspořádat direktivy using](#usings)
        - dotnet_sort_system_directives_first
- Nastavení formátování C#
    - [Možnosti nového řádku](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [Možnosti odsazení](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [Možnosti pro mezery](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
        - csharp_space_before_colon_in_inheritance_clause
        - csharp_space_after_colon_in_inheritance_clause
        - csharp_space_around_binary_operators
        - csharp_space_between_method_declaration_empty_parameter_list_parentheses
        - csharp_space_between_method_call_name_and_opening_parenthesis
        - csharp_space_between_method_call_empty_parameter_list_parentheses
    - [Nastavení zalamování](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>Nastavení formátování rozhraní .NET

Pravidla formátování v této části se vztahují na C# a Visual Basic.

#### <a name="usings"></a>Uspořádat direktivy using

Tato pravidla formátování se týká umístění System.* pomocí direktivy s ohledem na jiné direktivy using.

V následující tabulce jsou uvedeny název pravidla, použitelné jazyky, výchozí hodnoty a první podporovanou verzi sady Visual Studio:

| Název pravidla | Použitelné jazyky | Visual Studio výchozí | Visual Studio 2017 verze |
| ----------- | -------------------- | ----------------------| ---------------- |
| dotnet_sort_system_directives_first | C# a Visual Basic | true | 15.3 |

**dotnet\_sort\_system\_directives_first**

- Pokud toto pravidlo je nastaven na **true**řazení direktiv using abecedně System.* a umístit je před další direktivy using.
- Pokud toto pravidlo je nastaven na **false**, neumísťujte System.* pomocí direktivy před dalšími direktiv using.

Příklady kódu:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

Příklad *.editorconfig* souboru:

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
```

### <a name="c-formatting-settings"></a>Nastavení formátování C#

Formátování pravidla v této části se vztahují pouze na kód jazyka C#.

#### <a name="newline"></a>Možnosti nového řádku

Tato pravidla formátování se týkají používání nových řádků pro formátování kódu.

V následující tabulce jsou uvedeny "nový řádek" názvy pravidel použitelné jazyky, výchozí hodnoty a nejprve podporovanou verzi sady Visual Studio:

| Název pravidla | Použitelné jazyky | Visual Studio výchozí | Visual Studio 2017 verze |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_new_line_before_open_brace | C# | všechny | 15.3 |
| csharp_new_line_before_else | C# | true | 15.3 |
| csharp_new_line_before_catch | C# | true | 15.3 |
| csharp_new_line_before_finally | C# | true | 15.3 |
| csharp_new_line_before_members_in_object_initializers | C# | true | 15.3 |
| csharp_new_line_before_members_in_anonymous_types | C# | true | 15.3 |
| csharp_new_line_between_query_expression_clauses | C# | true | 15.3 |

**csharp\_new\_line\_before\_open_brace**

Toto pravidlo se týká, zda levou složenou závorku `{` by měly být umístěny na stejném řádku jako předchozí kód, nebo na nový řádek. Pro toto pravidlo nezadáte **true** nebo **false**. Místo toho zadáte **všechny**, **žádný**, nebo jeden nebo více prvky kódu, jako **metody** nebo **vlastnosti**, chcete-li definovat, kdy by měla být toto pravidlo použít. Úplný seznam povolených hodnot je uveden v následující tabulce:

| Hodnota | Popis
| ------------- |:-------------|
| přístupové objekty, anonymous_methods, anonymous_types, control_blocks, události, indexery, výrazů lambda, local_functions, metody, object_collection_array_initializers, vlastnosti, typy.<br>(Pro více typů, oddělte ","). | Požadování složených na nový řádek pro zadaný kód elementy (označované také jako "Allman" styl) |
| všechny | Požadování složených na nový řádek pro všechny výrazy ("Allman" styl) |
| žádná | Požadování složených být na stejném řádku pro všechny výrazy ("K & R") |

Příklady kódu:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**csharp\_new\_line\_before_else**

- Pokud toto pravidlo je nastaven na **true**, umístěte `else` příkazy na nový řádek.
- Pokud toto pravidlo je nastaven na **false**, umístěte `else` příkazy na stejném řádku.

Příklady kódu:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**csharp\_new\_line\_before_catch**

- Pokud toto pravidlo je nastaven na **true**, umístěte `catch` příkazy na nový řádek.
- Pokud toto pravidlo je nastaven na **false**, umístěte `catch` příkazy na stejném řádku.

Příklady kódu:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**csharp\_new\_line\_before_finally**

- Pokud toto pravidlo je nastaven na **true**, vyžadují `finally` příkazy následovat pravou složenou závorku na nový řádek.
- Pokud toto pravidlo je nastaven na **false**, vyžadují `finally` příkazy na stejném řádku jako pravou složenou závorku.

Příklady kódu:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**csharp\_new\_line\_before\_members\_in\_object_initializers**

- Pokud toto pravidlo je nastaven na **true**, vyžadují členy inicializátory objektů na samostatných řádcích.
- Pokud toto pravidlo je nastaven na **false**, vyžadují členy inicializátory objektů na stejném řádku.

Příklady kódu:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**csharp\_new\_line\_before\_members\_in\_anonymous_types**

- Pokud toto pravidlo je nastaven na **true**, vyžadují členy anonymních typů na samostatných řádcích.
- Pokud toto pravidlo je nastaven na **false**, vyžadují členy anonymních typů na stejném řádku.

Příklady kódu:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**

- Pokud toto pravidlo je nastaven na **true**, vyžadují prvky klauzule dotazového výrazu na samostatných řádcích.
- Pokud toto pravidlo je nastaven na **false**, vyžadují prvky klauzule dotazového výrazu na stejném řádku.

Příklady kódu:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

Příklad *.editorconfig* souboru:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="indent"></a>Možnosti odsazení

Tato pravidla formátování se týkají používání odsazení formátovat kód.

Následující tabulka uvádí názvy pravidel, použitelné jazyky, výchozí hodnoty a první podporovanou verzi sady Visual Studio:

| Název pravidla | Použitelné jazyky | Visual Studio výchozí | Visual Studio 2017 verze |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_indent_case_contents | C# | true | 15.3 |
| csharp_indent_switch_labels | C# | true | 15.3 |
| csharp_indent_labels | C# | no_change | 15.3 |

**csharp\_indent\_case_contents**

- Pokud toto pravidlo je nastaven na **true**, odsazení `switch` malá a velká obsah.
- Pokud toto pravidlo je nastaven na **false**, ne odsazení `switch` malá a velká obsah.

Příklady kódu:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent\_switch_labels**

- Pokud toto pravidlo je nastaven na **true**, odsazení `switch` popisky.
- Pokud toto pravidlo je nastaven na **false**, ne odsazení `switch` popisky.

Příklady kódu:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent_labels**

Toto pravidlo nepřijímá **true** nebo **false** hodnota; místo toho přijímá hodnotu z následující tabulky:

| Hodnota | Popis |
| ----- |:----------- |
| flush_left | Popisky jsou umístěny ve sloupci nejvíce vlevo |
| one_less_than_current | Popisky jsou umístěny na jednom méně odsazení aktuálního kontextu |
| no_change | Popisky jsou umístěny ve stejné odsazení jako aktuální kontext |

Příklady kódu:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

Příklad *.editorconfig* souboru:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="spacing"></a>Možnosti pro mezery

Tato pravidla formátování se týkají používání znaky mezery pro formátování kódu.

Následující tabulka uvádí názvy pravidel, použitelné jazyky, výchozí hodnoty a první podporovanou verzi sady Visual Studio:

| Název pravidla | Použitelné jazyky | Visual Studio výchozí | Visual Studio 2017 verze |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_space_after_cast | C# | false | 15.3 |
| csharp_space_after_keywords_in_control_flow_statements | C# | true | 15.3 |
| csharp_space_between_method_declaration_parameter_list_parentheses | C# | false | 15.3 |
| csharp_space_between_method_call_parameter_list_parentheses | C# | false | 15.3 |
| csharp_space_between_parentheses | C# | false | 15.3 |
| csharp_space_before_colon_in_inheritance_clause | C# | true | verzi 15.7 |
| csharp_space_after_colon_in_inheritance_clause | C# | true | verzi 15.7 |
| csharp_space_around_binary_operators | C# | before_and_after | verzi 15.7 |
| csharp_space_between_method_declaration_empty_parameter_list_parentheses | C# | false | verzi 15.7 |
| csharp_space_between_method_call_name_and_opening_parenthesis | C# | false | verzi 15.7 |
| csharp_space_between_method_call_empty_parameter_list_parentheses | C# | false | verzi 15.7 |

**csharp\_space\_after_cast**

- Pokud toto pravidlo je nastaven na **true**, vyžadují mezeru mezi přetypování a hodnotu.
- Pokud toto pravidlo je nastaven na **false**, vyžadují _žádné_ mezeru mezi přetypování a hodnotu.

Příklady kódu:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**

- Pokud toto pravidlo je nastaven na **true**, vyžadují mezera za klíčovým slovem v řídícím toku příkazů, jako `for` smyčky.
- Pokud toto pravidlo je nastaven na **false**, vyžadují _žádné_ mezera za klíčovým slovem v řídícím toku příkazů, jako `for` smyčky.

Příklady kódu:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**

- Pokud toto pravidlo je nastaven na **true**, umístěte znak mezery za levou (otevírací) a před pravou závorku seznamu parametrů deklarace metody.
- Pokud toto pravidlo je nastaven na **false**, neumísťujte znaky mezery za levou (otevírací) a před pravou závorku seznamu parametrů deklarace metody.

Příklady kódu:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**

- Pokud toto pravidlo je nastaven na **true**, umístěte znak mezery za levou (otevírací) a před pravou závorku volání metody.
- Pokud toto pravidlo je nastaven na **false**, neumísťujte znaky mezery za levou (otevírací) a před pravou závorku volání metody.

Příklady kódu:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**

Toto pravidlo je možné zadat jednu nebo více hodnot z následující tabulky:

| Hodnota | Popis |
| ----- |:------------|
| control_flow_statements | Vložit mezeru mezi závorky řídícího toku výrazů |
| výrazy | Vložit mezeru mezi závorky výrazů |
| type_casts | Vložit mezeru mezi závorky v přetypování typu |

Pokud můžete vynechat, nechte toto pravidlo, nebo použijte hodnotu jiné než `control_flow_statements`, `expressions`, nebo `type_casts`, nastavení se nepoužije.

Příklady kódu:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

**CSharp\_místo\_před\_dvojtečka\_v\_inheritance_clause**

- Pokud toto pravidlo je nastaven na **true**, vyžadují mezeru před dvojtečku pro základů nebo rozhraní v deklaraci typu.
- Pokud toto pravidlo je nastaven na **false**, vyžadují _žádné_ mezeru před dvojtečku pro základů nebo rozhraní v deklaraci typu.

Příklady kódu:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

**CSharp\_místo\_po\_dvojtečka\_v\_inheritance_clause**

- Pokud toto pravidlo je nastaven na **true**, vyžadují mezeru po dvojtečku pro základů nebo rozhraní v deklaraci typu.
- Pokud toto pravidlo je nastaven na **false**, vyžadují _žádné_ mezeru po dvojtečku pro základů nebo rozhraní v deklaraci typu.

Příklady kódu:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

**CSharp\_místo\_kolem\_binary_operators**

Toto pravidlo je možné zadat jednu hodnotu z následující tabulky:

| Hodnota | Popis |
| ----- |:------------|
| before_and_after | Vložit mezeru před a za binární operátor |
| žádná | Odebrat mezery před a za binární operátor |
| ignorovat | Ignorovat mezery kolem binárních operátorů |

Pokud můžete vynechat, nechte toto pravidlo, nebo použijte hodnotu jiné než `before_and_after`, `none`, nebo `ignore`, nastavení se nepoužije.

Příklady kódu:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

**csharp_space_between_method_declaration_empty_parameter_list_parentheses**

- Pokud toto pravidlo je nastaven na **true**, vložit mezeru mezi kulaté závorky seznamu prázdný parametr pro deklaraci metody.
- Pokud toto pravidlo je nastaven na **false**, odeberte mezeru mezi kulaté závorky seznamu prázdný parametr pro deklaraci metody.

Příklady kódu:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_name_and_opening_parenthesis**

- Pokud toto pravidlo je nastaven na **true**, vložit mezeru mezi název metody volání a levou závorku.
- Pokud toto pravidlo je nastaven na **false**, odebere mezeru mezi název metody volání a levou závorku.

Příklady kódu:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_empty_parameter_list_parentheses**

- Pokud toto pravidlo je nastaven na **true**, vložit mezeru mezi kulaté závorky prázdného seznamu argumentů.
- Pokud toto pravidlo je nastaven na **false**, odeberte mezeru mezi kulaté závorky prázdného seznamu argumentů.

Příklady kódu:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

Příklad *.editorconfig* souboru:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
```

#### <a name="wrapping"></a>Nastavení zalamování

Tato pravidla formátování se týkají používání jednotlivých řádků a samostatné řádky příkazů a bloků kódu.

Následující tabulka uvádí názvy pravidel, použitelné jazyky, výchozí hodnoty a první podporovanou verzi sady Visual Studio:

| Název pravidla | Použitelné jazyky | Visual Studio výchozí | Visual Studio 2017 verze |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_preserve_single_line_statements | C# | true | 15.3 |
| csharp_preserve_single_line_blocks | C# | true | 15.3 |

**csharp_preserve_single_line_statements**

- Pokud toto pravidlo je nastaven na **true**, nechat příkazy a člen deklarace na stejném řádku.
- Pokud toto pravidlo je nastaven na **false**, nechat příkazy a člen deklarace na samostatné řádky.

Příklady kódu:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

**csharp_preserve_single_line_blocks**

- Pokud toto pravidlo je nastaven na **true**, ponechte blok kódu na jednom řádku.
- Pokud toto pravidlo je nastaven na **false**, ponechte blok kódu na samostatných řádcích.

Příklady kódu:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

Příklad *.editorconfig* souboru:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="example-editorconfig-file"></a>Příklad souboru EditorConfig

Abyste mohli začít pracovat, tady je příklad *.editorconfig* soubor s výchozími možnostmi:

```EditorConfig
###############################
# Core EditorConfig Options   #
###############################

root = true

# All files
[*]
indent_style = space

# Code files
[*.{cs,csx,vb,vbx}]
indent_size = 4
insert_final_newline = true
charset = utf-8-bom

###############################
# .NET Coding Conventions     #
###############################

[*.{cs,vb}]
# Organize usings
dotnet_sort_system_directives_first = true

# this. preferences
dotnet_style_qualification_for_field = false:none
dotnet_style_qualification_for_property = false:none
dotnet_style_qualification_for_method = false:none
dotnet_style_qualification_for_event = false:none

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:none
dotnet_style_predefined_type_for_member_access = true:none

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:none
dotnet_style_readonly_field = true:suggestion

# Expression-level preferences
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent

###############################
# Naming Conventions          #
###############################

# Style Definitions
dotnet_naming_style.pascal_case_style.capitalization             = pascal_case

# Use PascalCase for constant fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.constant_fields_should_be_pascal_case.symbols  = constant_fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.style    = pascal_case_style
dotnet_naming_symbols.constant_fields.applicable_kinds            = field
dotnet_naming_symbols.constant_fields.applicable_accessibilities  = *
dotnet_naming_symbols.constant_fields.required_modifiers          = const

###############################
# C# Code Style Rules         #
###############################

[*.cs]
# var preferences
csharp_style_var_for_built_in_types = true:none
csharp_style_var_when_type_is_apparent = true:none
csharp_style_var_elsewhere = true:none

# Expression-bodied members
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:none
csharp_style_expression_bodied_indexers = true:none
csharp_style_expression_bodied_accessors = true:none

# Pattern-matching preferences
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion

# Null-checking preferences
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Expression-level preferences
csharp_prefer_braces = true:none
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion

###############################
# C# Formatting Rules         #
###############################

# New line preferences
csharp_new_line_before_open_brace = all
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left

# Space preferences
csharp_space_after_cast = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false

# Wrapping preferences
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true

##################################
# Visual Basic Code Style Rules  #
##################################

[*.vb]
# Modifier preferences
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

## <a name="see-also"></a>Viz také:

- [Rychlé akce](../ide/quick-actions.md)
- [Zásady vytváření názvů .NET pro EditorConfig](../ide/editorconfig-naming-conventions.md)
- [Vytvoření přenosné vlastního editoru](../ide/create-portable-custom-editor-options.md)
- [.NET compiler Platform .editorconfig file](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
