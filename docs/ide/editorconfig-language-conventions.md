---
title: Konvence jazyka .NET pro EditorConfig
ms.date: 03/31/2020
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a3f80eb555ef11a1e0a462e93d4508e778bd987d
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80544017"
---
# <a name="language-conventions"></a>Konvence jazyka

Jazykové konvence pro EditorConfig v sadě Visual Studio spadají do dvou kategorií: ty, které platí pro Visual Basic a C#, a ty, které jsou specifické pro C#. Jazykové konvence ovlivňují způsob použití různých aspektů programovacího jazyka, například modifikátory a závorky.

> [!TIP]
> - Chcete-li zobrazit příklady kódu v upřednostňovaném programovacím jazyce, zvolte jej pomocí výběru jazyka v pravém horním rohu okna prohlížeče.
>
>   ![Ovládací prvek výběru jazyka kódu](media/code-language-picker.png)
>
> - Pomocí odkazů **V tomto článku** přejděte na různé části stránky.

## <a name="rule-format"></a>Formát pravidla

Pravidla pro jazykové konvence mají následující obecný formát:

`option_name = value:severity`

Pro každou jazykovou konvenci určíte hodnotu, která definuje, zda nebo kdy má být daný styl preferován. Mnoho pravidel přijímá `true` hodnotu (preferují tento styl) nebo `false` (nedávají přednost tomuto stylu). Jiná pravidla přijímají `when_on_single_line` hodnoty, například nebo `never`. Druhá část pravidla určuje [závažnost](#severity-levels).

::: moniker range=">=vs-2019"

> [!NOTE]
> Vzhledem k tomu, že konvence jazyka jsou vynuceny analyzátory, můžete také nastavit jejich závažnost pomocí výchozí syntaxe konfigurace pro analyzátory. Syntaxe má `dotnet_diagnostic.<rule ID>.severity = <severity>`podobu , `dotnet_diagnostic.IDE0040.severity = silent`například . Další informace naleznete [v tématu Nastavení závažnosti pravidla v souboru EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file).

::: moniker-end

## <a name="severity-levels"></a>Úrovně závažnosti

Závažnost konvence jazyka určuje úroveň, na které chcete vynutit tento styl. V následující tabulce jsou uvedeny možné hodnoty závažnosti a jejich účinky:

Severity | Účinek
:------- | ------
`error` | Pokud je toto pravidlo stylu porušeno, zobrazte chybu kompilátoru.
`warning` | Pokud je toto pravidlo stylu porušeno, zobrazte upozornění kompilátoru.
`suggestion` | Pokud je toto pravidlo stylu porušeno, ukažte ho uživateli jako návrh. Návrhy se zobrazí jako tři šedé tečky pod prvními dvěma znaky.
`silent` | Nezobrazovat nic uživateli, pokud je toto pravidlo porušeno. Funkce generování kódu však generují kód v tomto stylu. Pravidla `silent` se závažností se účastní čištění a zobrazují se v nabídce **Rychlé akce a Refaktoringy.**
`none` | Nezobrazovat nic uživateli, pokud je toto pravidlo porušeno. Funkce generování kódu však generují kód v tomto stylu. Pravidla `none` se závažností se nikdy nezobrazí v nabídce **Rychlé akce a Refaktorings.** Ve většině případů je to považováno za "zakázáno" nebo "ignorováno".

::: moniker range=">=vs-2019"

## <a name="automatically-configure-code-styles"></a>Automatická konfigurace stylů kódu

Počínaje Visual Studio 2019 verze 16.3, můžete nakonfigurovat pravidla stylu kódu z nabídky rychlé [akce](quick-actions.md) žárovky po porušení stylu dojde.

Změna konvence stylu kódu:

1. Najeďte přes vlnovku v editoru a otevřete nabídku žárovky, která se zobrazí. Zvolte **Konfigurovat nebo potlačit problémy** > **Konfigurace \<ID pravidla> stylu kódu**.

   ![Konfigurace stylu kódu z nabídky žárovky v sadě Visual Studio](media/vs-2019/configure-code-style.png)

2. Odtud zvolte jednu z možností stylu kódu.

   ![Konfigurace nastavení stylu kódu](media/vs-2019/configure-code-style-setting.png)

   Visual Studio přidá nebo upraví nastavení konfigurace v souboru EditorConfig, jak je znázorněno v poli náhledu.

Chcete-li změnit závažnost porušení stylu kódu, postupujte stejným způsobem, ale zvolte **Konfigurovat \<ID pravidla> závažnosti** namísto **konfigurovat \<ID pravidla> stylu kódu**. Další informace naleznete v tématu [Automaticky konfigurovat závažnost pravidla](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity).

::: moniker-end

## <a name="net-code-style-settings"></a>Nastavení stylu kódu .NET

Pravidla stylu v této části platí pro c# a visual basic.

- ["Toto." a "Já" kvalifikace](#this-and-me)
  - dotnet\_\_styl\_kvalifikace for_field
  - dotnet\_\_styl\_kvalifikace for_property
  - dotnet\_\_styl\_kvalifikace for_method
  - dotnet\_\_styl\_kvalifikace for_event
- [Jazyková klíčová slova namísto názvů typů architektury pro odkazy na typ](#language-keywords)
  - předdefinovaný\_\_typ\_\_stylu dotnet pro\_místní parameters_members\_
  - předdefinovaný\_\_text\_\_stylu dotnet pro\_member_access
- [Předvolby modifikátoru](#normalize-modifiers)
  - dotnet\_\_styl\_vyžadují accessibility_modifiers
  - \_přednostní\_modifier_order jazyka\_
  - Pole jen\_\_pro\_čtení stylu dotnet
- [Předvolby závorek](#parentheses-preferences)
  - Závorky\_stylu dotnet\_v\_\_aritmetických binárních\_operátorech\_
  - Závorky\_stylu dotnet\_\_v\_\_jiných binárních\_operátorech
  - Závorky\_ve stylu\_\_dotnet\_\_v jiných operátorech
  - Závorky\_stylu dotnet\_\_v\_\_\_relačních binárních operátorech
- [Předvolby na úrovni výrazu](#expression-level-preferences)
  - object_initializer stylu\_\_dotnet
  - dotnet\_\_styl collection_initializer
  - explicitní\_tuple_names\_\_stylu dotnet
  - dotnet\_\_styl\_raději\_odvodit tuple_names
  - Dotnet\_\_styl\_preferují\_\_odvozené\_anonymní typ member_names
  - dotnet\_\_styl\_\_preferují automatické vlastnosti
  - Dotnet\_\_styl\_\_upřednostňovat podmíněný výraz\_před přiřazením\_
  - Dotnet\_\_styl\_\_upřednostňovat podmíněný výraz\_před návratem\_
  - Dotnet\_\_styl\_\_preferují složené přiřazení
- [Předvolby kontroly "Null"](#null-checking-preferences)
  - coalesce_expression stylu\_\_dotnet
  - null_propagation stylu\_\_dotnet
  - Dotnet\_\_styl\_\_preferuje\_\_je\_kontrola null\_\_nad metodou rovnosti odkazů

### <a name="this-and-me-qualifiers"></a><a name="this-and-me"></a>"Tohle." a "Já". Kvalifikátory

Toto pravidlo stylu lze použít pro pole, vlastnosti, metody nebo události. Hodnota **true** znamená přednost symbol kódu, které `this.` mají být `Me.` předchází v jazyce C# nebo v jazyce Visual Basic. Hodnota **false** znamená upřednostnit prvek _kódu,_ které nemají být předchází `this.` nebo `Me.`.

Tato pravidla se mohou v souboru *.editorconfig* zobrazit následujícím způsobem:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>dotnet\_\_styl\_kvalifikace for_field

|||
|-|-|
| **Název pravidla** | dotnet_style_qualification_for_field |
| **ID pravidla** | IDE0003 a IDE0009 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferovat pole, `this.` která mají `Me.` být předcpané v jazyce C# nebo v jazyce Visual Basic<br /><br />`false`- Upřednostnit pole, `this.` která _nemají_ být předchází nebo`Me.` |
| **Výchozí nastavení sady Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_property"></a>dotnet\_\_styl\_kvalifikace for_property

|||
|-|-|
| **Název pravidla** | dotnet_style_qualification_for_property |
| **ID pravidla** | IDE0003 a IDE0009 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferovat vlastnosti, `this.` které mají `Me.` být předchází v jazyce C# nebo v jazyce Visual Basic<br /><br />`false`- Upřednostnit vlastnosti, které _nemají_ být předchází `this.` nebo`Me.` |
| **Výchozí nastavení sady Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_method"></a>dotnet\_\_styl\_kvalifikace for_method

|||
|-|-|
| **Název pravidla** | dotnet_style_qualification_for_method |
| **ID pravidla** | IDE0003 a IDE0009 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferovat metody, `this.` které mají `Me.` být předchází v jazyce C# nebo v jazyce Visual Basic.<br /><br />`false`- Preferují metody, `this.` které `Me.` _nemají_ být předchází nebo . |
| **Výchozí nastavení sady Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_event"></a>dotnet\_\_styl\_kvalifikace for_event

|||
|-|-|
| **Název pravidla** | dotnet_style_qualification_for_event |
| **ID pravidla** | IDE0003 a IDE0009 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferovat události, `this.` které mají `Me.` být předchází v jazyce C# nebo v jazyce Visual Basic.<br /><br />`false`- Upřednostnit _události,_ které nemají být předchází `this.` nebo `Me.`. |
| **Výchozí nastavení sady Visual Studio** | `false:silent` |

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

### <a name="language-keywords-instead-of-framework-type-names-for-type-references"></a><a name="language-keywords"></a>Jazyková klíčová slova namísto názvů typů architektury pro odkazy na typ

Toto pravidlo stylu lze použít pro místní proměnné, parametry metody a členy třídy nebo jako samostatné pravidlo pro výrazy přístupu členů. Hodnota **true** znamená preferovat klíčové slovo `int` jazyka `Integer`(například nebo ) místo `Int32`názvu typu (například) pro typy, které mají klíčové slovo, které je představuje. Hodnota **false** znamená preferují název typu namísto klíčového slova jazyka.

Tato pravidla se mohou v souboru *.editorconfig* zobrazit následujícím způsobem:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>předdefinovaný\_\_typ\_\_stylu dotnet pro\_místní parameters_members\_

|||
|-|-|
| **Název pravidla** | dotnet_style_predefined_type_for_locals_parameters_members |
| **ID pravidla** | IDE0012 a IDE0014 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferují klíčové slovo jazyka pro místní proměnné, parametry metody a členy třídy, namísto názvu typu, pro typy, které mají klíčové slovo, které je představuje<br /><br />`false`- Preferují název typu pro místní proměnné, parametry metody a členy třídy, místo klíčového slova jazyka |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

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

#### <a name="dotnet_style_predefined_type_for_member_access"></a>předdefinovaný\_\_text\_\_stylu dotnet pro\_member_access

|||
|-|-|
| **Název pravidla** | dotnet_style_predefined_type_for_member_access |
| **ID pravidla** | IDE0013 a IDE0015 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferují klíčové slovo jazyka pro výrazy členské přístupu, místo názvu typu, pro typy, které mají klíčové slovo k jejich reprezentaci<br /><br />`false`- Preferují název typu pro výrazy přístupu členů, místo klíčového slova jazyka |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

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

### <a name="modifier-preferences"></a><a name="normalize-modifiers"></a>Předvolby modifikátoru

Pravidla stylu v této části se týkají předvoleb modifikátorů, včetně vyžadování modifikátorů usnadnění, určení požadovaného pořadí řazení modifikátoru a vyžadování modifikátoru jen pro čtení.

Tato pravidla se mohou v souboru *.editorconfig* zobrazit následujícím způsobem:

```ini
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

#### <a name="dotnet_style_require_accessibility_modifiers"></a>dotnet\_\_styl\_vyžadují accessibility_modifiers

|||
|-|-|
| **Název pravidla** | dotnet_style_require_accessibility_modifiers |
| **ID pravidla** | IDE0040 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always`- Upřednostňujte modifikátory usnadnění přístupu, které mají být zadány.<br /><br />`for_non_interface_members`- Upřednostňujte modifikátory usnadnění, které mají být deklarovány s výjimkou členů veřejného rozhraní. (To je stejné jako **vždy** a byl přidán pro budoucí protečování, pokud C# přidá výchozí metody rozhraní.)<br /><br />`never`- Neupřednostňujte modifikátory přístupnosti, které mají být zadány.<br /><br />`omit_if_default`- Preferovat modifikátory usnadnění, které mají být určeny, s výjimkou případů, kdy jsou výchozí modifikátor. |
| **Výchozí nastavení sady Visual Studio** | `for_non_interface_members:silent` |
| **Zavedená verze** | Visual Studio 2017 verze 15.5 |

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

#### <a name="csharp_preferred_modifier_order"></a>csharp_preferred_modifier_order

|||
|-|-|
| **Název pravidla** | csharp_preferred_modifier_order |
| **ID pravidla** | IDE0036 |
| **Použitelné jazyky** | C# |
| **Hodnoty** | Jeden nebo více modifikátorů `public` `private`Jazyka C#, například , a`protected` |
| **Výchozí nastavení sady Visual Studio** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Zavedená verze** | Visual Studio 2017 verze 15.5 |

- Pokud je toto pravidlo nastaveno na seznam modifikátorů, upřednostňujte zadané řazení.
- Pokud je toto pravidlo ze souboru vynecháno, neupřednostňujte pořadí modifikátorů.

Příklady kódu:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

#### <a name="visual_basic_preferred_modifier_order"></a>visual_basic_preferred_modifier_order

|||
|-|-|
| **Název pravidla** | visual_basic_preferred_modifier_order |
| **ID pravidla** | IDE0036 |
| **Použitelné jazyky** | Visual Basic |
| **Hodnoty** | Jeden nebo více modifikátorů `Partial` `Private`jazyka Visual Basic, například , a`Public` |
| **Výchozí nastavení sady Visual Studio** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Zavedená verze** | Visual Studio 2017 verze 15.5 |

- Pokud je toto pravidlo nastaveno na seznam modifikátorů, upřednostňujte zadané řazení.
- Pokud je toto pravidlo ze souboru vynecháno, neupřednostňujte pořadí modifikátorů.

Příklady kódu:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="visual_basic_style_unused_value_expression_statement_preference"></a>visual_basic_style_unused_value_expression_statement_preference

|||
|-|-|
| **Název pravidla** | visual_basic_style_unused_value_expression_statement_preference |
| **ID pravidla** | IDE0058 |
| **Použitelné jazyky** | Visual Basic |
| **Hodnoty** | `unused_local_variable:silent` |
| **Výchozí nastavení sady Visual Studio** | `unused_local_variable:silent` |

Příklady kódu:

```vb
' visual_basic_style_unused_value_expression_statement_preference = unused_local_variable:silent

Dim unused = Computation()
```

#### <a name="visual_basic_style_unused_value_assignment_preference"></a>visual_basic_style_unused_value_assignment_preference

|||
|-|-|
| **Název pravidla** | visual_basic_style_unused_value_assignment_preference |
| **ID pravidla** | IDE0059 |
| **Použitelné jazyky** | Visual Basic |
| **Hodnoty** | `unused_local_variable:silent` |
| **Výchozí nastavení sady Visual Studio** | `unused_local_variable:silent` |

Příklady kódu:

```vb
' visual_basic_style_unused_value_assignment_preference = unused_local_variable:suggestion

Dim unused = Computation()
Dim x = 1;
```

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|||
|-|-|
| **Název pravidla** | dotnet_style_readonly_field |
| **ID pravidla** | IDE0044 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferovat, že `readonly` pole by měla `ReadOnly` být označena (C#) nebo (Visual Basic), pokud jsou pouze někdy přiřazeny vřádku, nebo uvnitř konstruktoru<br /><br />`false`- Nezadejte žádné preference před `readonly` tím, zda `ReadOnly` mají být pole označena (C#) nebo (Visual Basic) |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Zavedená verze** | Visual Studio 2017 verze 15.7 |

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

### <a name="parentheses-preferences"></a>Předvolby závorek

Pravidla stylu v této části se týkají předvoleb závorek, včetně použití závorek pro aritmetické, relační a jiné binární operátory.

Tato pravidla se mohou v souboru *.editorconfig* zobrazit následujícím způsobem:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>\_závorky\_\_stylu dotnet v\_\_aritmetickém binary_operators

|||
|-|-|
| **Název pravidla** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **ID pravidla** | IDE0047 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always_for_clarity`- Preferujte závorky k objasnění `/` `%`aritmetické priority `^` `|`(`*`, , `+`, `-`, `<<` `>>`, `&`, , , )<br /><br />`never_if_unnecessary`- Upřednostňujte nemít závorky,`*`když `/` `%`je `+` `-`aritmetický `^` `|`operátor ( , , , , `<<` `>>`, `&`, , , ) priorita zřejmá |
| **Výchozí nastavení sady Visual Studio** | `always_for_clarity:silent` |
| **Zavedená verze** | Visual Studio 2017 verze 15.8 |

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

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>\_závorky\_\_stylu dotnet\_\_v relačních binary_operators

|||
|-|-|
| **Název pravidla** | dotnet_style_parentheses_in_relational_binary_operators |
| **ID pravidla** | IDE0047 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always_for_clarity`- Upřednostnit závorky`>`k `<` `<=`objasnění relačního operátoru ( , `>=`, , `is` `as`, `==` `!=`, ) priority<br /><br />`never_if_unnecessary`- Upřednostňujte nemít závorky, `<` `<=`když `>=` `is`je `as` `==`zřejmý `!=`relační operátor (`>`, , , , , , , ) |
| **Výchozí nastavení sady Visual Studio** | `always_for_clarity:silent` |
| **Zavedená verze** | Visual Studio 2017 verze 15.8 |

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

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>\_závorky\_\_stylu dotnet v\_jiných\_binary_operators

|||
|-|-|
| **Název pravidla** | dotnet_style_parentheses_in_other_binary_operators |
| **ID pravidla** | IDE0047 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always_for_clarity`- Upřednostňujte závorky,`&&` `||`aby `??`se vyjasnily další binární operátor ( , , ) prioritu<br /><br />`never_if_unnecessary`- Upřednostňujte nemít závorky, `||` `??`když je zřejmý jiný binární operátor (`&&`, , ) priorita |
| **Výchozí nastavení sady Visual Studio** | `always_for_clarity:silent` |
| **Zavedená verze** | Visual Studio 2017 verze 15.8 |

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

#### <a name="dotnet_style_parentheses_in_other_operators"></a>\_Závorky\_\_stylu dotnet v\_other_operators

|||
|-|-|
| **Název pravidla** | dotnet_style_parentheses_in_other_operators |
| **ID pravidla** | IDE0047 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always_for_clarity`- Preferují závorky k objasnění priority operátora<br /><br />`never_if_unnecessary`- Raději nemají závorky, když je zřejmé, že priorita operátoru je zřejmá |
| **Výchozí nastavení sady Visual Studio** | `never_if_unnecessary:silent` |
| **Zavedená verze** | Visual Studio 2017 verze 15.8 |

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

### <a name="expression-level-preferences"></a>Předvolby na úrovni výrazu

Pravidla stylu v této části se týkají předvoleb na úrovni výrazu, včetně použití inicializačních prvků objektu, inicializátorů kolekce, explicitních nebo odvozených názvů řazených členů řazené kolekce členů a odvozených anonymních typů.

Tato pravidla se mohou v souboru *.editorconfig* zobrazit následujícím způsobem:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
dotnet_style_prefer_compound_assignment = true:suggestion
```

#### <a name="dotnet_style_object_initializer"></a>object_initializer stylu\_\_dotnet

|||
|-|-|
| **Název pravidla** | dotnet_style_object_initializer |
| **ID pravidla** | IDE0017 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferovat objekty, které mají být inicializovány pomocí inicializačních objektů, pokud je to možné<br /><br />`false`- Preferovat *objekty,* které nemají být inicializovány pomocí objektu inicializačních objektů |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_collection_initializer"></a>dotnet\_\_styl collection_initializer

|||
|-|-|
| **Název pravidla** | dotnet_style_collection_initializer |
| **ID pravidla** | IDE0028 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferují kolekce, které mají být inicializovány pomocí inicializačních inicializátorů kolekce, pokud je to možné<br /><br />`false`- Preferují *kolekce,* které nemají být inicializovány pomocí inicializačních iniciátorů kolekce |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_explicit_tuple_names"></a>explicitní\_tuple_names\_\_stylu dotnet

|||
|-|-|
| **Název pravidla** | dotnet_style_explicit_tuple_names |
| **ID pravidla** | IDE0033 |
| **Použitelné jazyky** | C# 7.0+ a Visual Basic 15+ |
| **Hodnoty** | `true`- Preferují názvy řazené kolekce členů před vlastnostmi ItemX<br /><br />`false`- Upřednostnit ItemX vlastnosti řazené kolekce členů názvy |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>dotnet\_\_styl\_raději\_odvodit tuple_names

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_inferred_tuple_names |
| **ID pravidla** | IDE0037 |
| **Použitelné jazyky** | C# 7.1+ a Visual Basic 15+ |
| **Hodnoty** | `true`- Preferovat odvozené názvy prvků řazené kolekce členů<br /><br />`false`- Preferují explicitní názvy prvků řazené kolekce členů |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Zavedená verze** | Visual Studio 2017 verze 15.6 |

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

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>Dotnet\_\_styl\_preferují\_\_odvozené\_anonymní typ member_names

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **ID pravidla** | IDE0037 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferujte odvozená anonymní jména členů typu<br /><br />`false`- Preferují explicitní anonymní názvy členů typu |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Zavedená verze** | Visual Studio 2017 verze 15.6 |

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

#### <a name="dotnet_style_prefer_auto_properties"></a>dotnet\_\_styl\_\_preferují automatické vlastnosti

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_auto_properties |
| **ID pravidla** | IDE0032 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Upřednostnit autoproperties před vlastnostmi s privátními doprovodnými poli<br /><br />`false`- Preferovat vlastnosti se soukromými doprovodnými poli před automatickými vlastnostmi |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Zavedená verze** | Visual Studio 2017 verze 15.7 |

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

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>Dotnet\_\_styl\_\_preferuje\_\_je\_kontrola null\_\_nad metodou rovnosti odkazů

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **ID pravidla** | IDE0041 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferujte použití nulové kontroly s porovnáváním vzorů`object.ReferenceEquals`<br /><br />`false`- `object.ReferenceEquals` Preferují před nulovou kontrolu s vzor-odpovídající |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Zavedená verze** | Visual Studio 2017 verze 15.7 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>dotnet\_\_styl\_\_preferují podmíněný výraz\_over_assignment

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_conditional_expression_over_assignment |
| **ID pravidla** | IDE0045 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferovat přiřazení s ternární podmíněnou přes if-else prohlášení<br /><br />`false`- Preferují přiřazení s příkazem if-else před ternární montovnou |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Zavedená verze** | Visual Studio 2017 verze 15.8 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>dotnet\_\_styl\_\_preferují podmíněný výraz\_over_return

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_conditional_expression_over_return |
| **ID pravidla** | IDE0046 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Upřednostňujte příkazy vrácení pro použití ternární podmíněné před příkazem if-else.<br /><br />`false`- Preferovat příkazy vrácení použít if-else prohlášení přes ternární podmíněné |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Zavedená verze** | Visual Studio 2017 verze 15.8 |

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

#### <a name="dotnet_style_prefer_compound_assignment"></a>Dotnet\_\_styl\_\_preferují složené přiřazení

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_compound_assignment |
| **ID pravidla** | IDE0054 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferují složené výrazy [přiřazení](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment)<br /><br />`false`- Nepreferujte složené výrazy přiřazení |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// dotnet_style_prefer_compound_assignment = true
x += 1;

// dotnet_style_prefer_compound_assignment = false
x = x + 1;
```

```vb
' dotnet_style_prefer_compound_assignment = true
x += 1

' dotnet_style_prefer_compound_assignment = false
x = x + 1
```

### <a name="null-checking-preferences"></a>Předvolby kontroly null

Pravidla stylu v této části se týkají předvoleb kontroly null.

Tato pravidla se mohou v souboru *.editorconfig* zobrazit následujícím způsobem:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
```

#### <a name="dotnet_style_coalesce_expression"></a>coalesce_expression stylu\_\_dotnet

|||
|-|-|
| **Název pravidla** | dotnet_style_coalesce_expression |
| **ID pravidla** | IDE0029 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`- Preferovat nulové slučování výrazy ternární operátor kontrolu<br /><br />`false`- Upřednostňujte kontrolu ternárního operátora před nulovým slučováním výrazů. |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_null_propagation"></a>null_propagation stylu\_\_dotnet

|||
|-|-|
| **Název pravidla** | dotnet_style_null_propagation |
| **ID pravidla** | IDE0031 |
| **Použitelné jazyky** | C# 6.0+ a Visual Basic 14+ |
| **Hodnoty** | `true`- Raději používat operátor s nulovou podmínkou, pokud je to možné<br /><br />`false`- Raději používat ternární kontrolu nula, pokud je to možné |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

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

### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>Dotnet\_\_styl\_\_preferuje\_\_je\_kontrola null\_\_nad metodou rovnosti odkazů

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **ID pravidla** | IDE0041 |
| **Použitelné jazyky** | C# 6.0+ a Visual Basic 14+ |
| **Hodnoty** | `true`- Prefer je null check over reference equality method<br /><br />`false`- Preferovat referenční metodu rovnosti nad je kontrola null |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

## <a name="net-code-quality-settings"></a>Nastavení kvality kódu .NET

Pravidla kvality v této části platí pro kód jazyka C# i jazyka Visual Basic. Používají se ke konfiguraci analyzátory kódu, které jsou integrovány do integrovaného vývojového prostředí Visual Studio (IDE). Informace o konfiguraci analyzátorů FxCop pomocí souboru EditorConfig naleznete v [tématu Konfigurace analyzátorů FxCop](../code-quality/configure-fxcop-analyzers.md).

- [Předvolby parametrů](#parameter-preferences)
  - dotnet\_\_kód\_kvality\_nepoužívané parametry

### <a name="parameter-preferences"></a>Předvolby parametrů

Pravidla kvality v této části se týkají parametrů metody.

Tato pravidla se mohou v souboru *.editorconfig* zobrazit následujícím způsobem:

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>dotnet\_\_kód\_kvality\_nepoužívané parametry

|||
|-|-|
| **Název pravidla** | dotnet_code_quality_unused_parameters |
| **ID pravidla** | IDE0060 |
| **Použitelné jazyky** | C# a Visual Basic |
| **Hodnoty** | `all`- Flag metody s přístupností, které obsahují nepoužívané parametry<br /><br />`non_public`- Příznak pouze neveřejné metody, které obsahují nepoužívané parametry |
| **Výchozí nastavení sady Visual Studio** | `all:suggestion` |

Příklady kódu:

```csharp
// dotnet_code_quality_unused_parameters = all:suggestion
public int GetNum() { return 1; }

// dotnet_code_quality_unused_parameters = non_public:suggestion
public int GetNum(int arg1) { return 1; }
```

```vb
' dotnet_code_quality_unused_parameters = all:suggestion
Public Function GetNum()
    Return 1
End Function

' dotnet_code_quality_unused_parameters = non_public:suggestion
Public Function GetNum(arg1 As Integer)
    Return 1
End Function
```

## <a name="c-code-style-settings"></a>Nastavení stylu kódu jazyka C#

Pravidla stylu v této části platí pouze pro C#.

- [Implicitní a explicitní typy](#implicit-and-explicit-types)
  - csharp\_\_style\_\_var\_pro postavené in_types
  - csharp\_\_style\_\_var\_při is_apparent
  - csharp\_\_styl var_elsewhere
- [Členové tvoření výrazy](#expression-bodied-members)
  - výraz\_\_stylu\_csharp bodied_methods
  - výraz\_\_stylu\_csharp bodied_constructors
  - výraz\_\_stylu\_csharp bodied_operators
  - výraz\_\_stylu\_csharp bodied_properties
  - výraz\_\_stylu\_csharp bodied_indexers
  - csharp\_\_styl\_výraz bodied_accessors
  - výraz\_\_stylu\_csharp bodied_lambdas
  - výraz\_stylu\_\_csharp\_local_functions
- [Porovnávání](#pattern-matching)
  - csharp\_\_styl\_\_vzor\_\_odpovídající\_přes je s cast_check
  - csharp\_\_styl\_\_vzor\_\_odpovídající\_přes jako u null_check
- [Vložené deklarace proměnných](#inlined-variable-declarations)
  - styl\_csharp\_\_vložený variable_declaration
- [Předvolby na úrovni výrazu](#c-expression-level-preferences)
  - csharp\_\_preferují jednoduché\_default_expression
- [Předvolby kontroly "Null"](#c-null-checking-preferences)
  - csharp\_\_styl throw_expression
  - podmíněný\_\_delegate_call\_stylu csharp
- [Předvolby modifikátoru](#normalize-modifiers)
  - csharp\_\_preferoval modifier_order
- [Předvolby bloku kódu](#code-block-preferences)
  - csharp\_prefer_braces
- [Předvolby nevyužitých hodnot](#unused-value-preferences)
  - csharp\_\_styl\_nevyužité hodnoty\_výraz\_statement_preference
  - csharp\_\_styl\_nevyužité hodnoty\_assignment_preference
- [Index a předvolby rozsahu](#index-and-range-preferences)
  - csharp\_\_styl\_preferují index_operator
  - csharp\_\_styl\_preferují range_operator
- [Různé preference](#miscellaneous-preferences)
  - csharp\_\_styl deconstructed\_variable_declaration
  - csharp\_\_styl\_\_vzor\_místní přes anonymous_function
  - csharp\_\_pomocí\_umístění direktivy
  - csharp\_\_preferují statické\_local_function
  - csharp\_\_preferují jednoduché\_using_statement
  - csharp\_\_styl\_preferují switch_expression

### <a name="implicit-and-explicit-types"></a>Implicitní a explicitní typy

Pravidla stylu v této části se týkají použití klíčového slova [var](/dotnet/csharp/language-reference/keywords/var) versus explicitního typu v deklaraci proměnné. Toto pravidlo lze použít samostatně na předdefinované typy, pokud je typ zřejmý, a jinde.

Příklad souboru *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharp_style_var_for_built_in_types"></a>csharp\_\_style\_\_var\_pro postavené in_types

|||
|-|-|
| **Název pravidla** | csharp_style_var_for_built_in_types |
| **ID pravidla** | IDE0007 a IDE0008 |
| **Použitelné jazyky** | C#  |
| **Hodnoty** | `true`- `var` Preferpoužívá se k deklarování proměnných s vestavěnými typy systémů, jako jsou`int`<br /><br />`false`- Upřednostňujte explicitní typ před `var` deklarovat proměnné s vestavěnými typy systému, jako jsou`int` |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>csharp\_\_style\_\_var\_při is_apparent

|||
|-|-|
| **Název pravidla** | csharp_style_var_when_type_is_apparent |
| **ID pravidla** | IDE0007 a IDE0008 |
| **Použitelné jazyky** | C#  |
| **Hodnoty** | `true`- `var` Preferovat, když typ je již uvedeno na pravé straně prohlášení výrazu<br /><br />`false`- Upřednostňujte explicitní typ, `var` pokud je typ již uveden na pravé straně výrazu deklarace |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>csharp\_\_styl var_elsewhere

|||
|-|-|
| **Název pravidla** | csharp_style_var_elsewhere |
| **ID pravidla** | IDE0007 a IDE0008 |
| **Použitelné jazyky** | C#  |
| **Hodnoty** | `true`- `var` Upřednostňujte explicitní typ ve všech případech, pokud není přepsán jiným pravidlem stylu kódu<br /><br />`false`- Preferovat `var` explicitní typ ve všech případech, pokud není přepsán jiným pravidlem stylu kódu |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>Členové tvoření výrazy

Pravidla stylu v této části se týkají použití [členů s výrazem,](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) pokud se logika skládá z jednoho výrazu. Toto pravidlo lze použít pro metody, konstruktory, operátory, vlastnosti, indexery a přistupující objekty.

Příklad souboru *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
```

#### <a name="csharp_style_expression_bodied_methods"></a>výraz\_\_stylu\_csharp bodied_methods

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_methods |
| **ID pravidla** | IDE0022 |
| **Použitelné jazyky** | C# 6.0+  |
| **Hodnoty** | `true`- Preferovat těla výrazů pro metody<br /><br />`when_on_single_line`- Preferovat těla výrazů pro metody, když budou jeden řádek<br /><br />`false`- Preferují bloková těla pro metody |
| **Výchozí nastavení sady Visual Studio** | `false:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>výraz\_\_stylu\_csharp bodied_constructors

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_constructors |
| **ID pravidla** | IDE0021 |
| **Použitelné jazyky** | C# 7.0+ |
| **Hodnoty** | `true`- Preferovat těla výrazů pro konstruktory<br /><br />`when_on_single_line`- Preferovat těla výrazů pro konstruktory, když budou jeden řádek<br /><br />`false`- Preferují bloková těla pro konstruktéry |
| **Výchozí nastavení sady Visual Studio** | `false:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>výraz\_\_stylu\_csharp bodied_operators

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_operators |
| **ID pravidla** | IDE0023 a IDE0024 |
| **Použitelné jazyky** | C# 7.0+ |
| **Hodnoty** | `true`- Preferovat těla výrazů pro operátory<br /><br />`when_on_single_line`- Preferovat těla výrazů pro operátory, když budou jeden řádek<br /><br />`false`- Preferují blokové nástavby pro operátory |
| **Výchozí nastavení sady Visual Studio** | `false:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharp_style_expression_bodied_properties"></a>výraz\_\_stylu\_csharp bodied_properties

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_properties |
| **ID pravidla** | IDE0025 |
| **Použitelné jazyky** | C# 7.0+ |
| **Hodnoty** | `true`- Preferovat těla výrazů pro vlastnosti<br /><br />`when_on_single_line`- Preferovat těla výrazů pro vlastnosti, když budou jeden řádek<br /><br />`false`- Preferují bloková těla pro vlastnosti |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>výraz\_\_stylu\_csharp bodied_indexers

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_indexers |
| **ID pravidla** | IDE0026 |
| **Použitelné jazyky** | C# 7.0+ |
| **Hodnoty** | `true`- Preferovat těla výrazů pro indexery<br /><br />`when_on_single_line`- Preferovat těla výrazů pro indexery, když budou jeden řádek<br /><br />`false`- Preferují bloková těla pro indexery |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>csharp\_\_styl\_výraz bodied_accessors

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_accessors |
| **ID pravidla** | IDE0027 |
| **Použitelné jazyky** | C# 7.0+ |
| **Hodnoty** | `true`- Preferovat těla výrazů pro přistupující subjekty<br /><br />`when_on_single_line`- Preferovat těla výrazů pro přistupující subjekty, když budou jeden řádek<br /><br />`false`- Preferují bloková těla pro přistupující subjekty |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>výraz\_\_stylu\_csharp bodied_lambdas

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_lambdas |
| **ID pravidla** | IDE0053 |
| **Hodnoty** | `true`- Preferujte těla výrazů pro lambdy<br /><br />`when_on_single_line`- Preferují těla výrazů pro lambdy, když budou jeden řádek<br /><br />`false`- Preferují blokové nástavby pro lambdy |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>výraz\_stylu\_\_csharp\_local_functions

Počínaje c# 7.0, C# podporuje [místní funkce](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Místní funkce jsou soukromé metody typu, které jsou vnořeny v jiném členu.

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_local_functions |
| **ID pravidla** | IDE0061 |
| **Použitelné jazyky** | C# 7.0+ |
| **Hodnoty** | `true`- Preferovat těla výrazů pro místní funkce<br /><br />`when_on_single_line`- Preferovat těla výrazů pro místní funkce, když budou jeden řádek<br /><br />`false`- Preferují bloková těla pro místní funkce |
| **Výchozí nastavení sady Visual Studio** | `false:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_local_functions = true
void M()
{
    Hello();
    void Hello() => Console.WriteLine("Hello");
}

// csharp_style_expression_bodied_local_functions = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

### <a name="pattern-matching"></a>Porovnávání vzorů

Pravidla stylu v této části se týkají použití [porovnávání vzorů](/dotnet/csharp/pattern-matching) v c#.

Příklad souboru *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>csharp\_\_styl\_\_vzor\_\_odpovídající\_přes je s cast_check

|||
|-|-|
| **Název pravidla** | csharp_style_pattern_matching_over_is_with_cast_check |
| **ID pravidla** | IDE0020 |
| **Použitelné jazyky** | C# 7.0+ |
| **Hodnoty** | `true`- Preferují `is` porovnávání vzorů namísto výrazů s přetypováním<br /><br />`false`- `is` Preferují výrazy s přetypování maže místo porovnávání vzorů |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>csharp\_\_styl\_\_vzor\_\_odpovídající\_přes jako u null_check

|||
|-|-|
| **Název pravidla** | csharp_style_pattern_matching_over_as_with_null_check |
| **ID pravidla** | IDE0019 |
| **Použitelné jazyky** | C# 7.0+ |
| **Hodnoty** | `true`- Preferovat porovnávání vzorů namísto `as` výrazů s nulovými kontrolami, abyste zjistili, zda je něco určitého typu<br /><br />`false`- `as` Preferovat výrazy s null kontroly namísto porovnávání vzorů k určení, zda je něco určitého typu |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>Vložené deklarace proměnných

Toto pravidlo `out` stylu se týká toho, zda jsou proměnné deklarovány jako vložkové či nikoli. Počínaje C# 7, můžete [deklarovat out proměnné v seznamu argument volání metody](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), nikoli v samostatné deklaraci proměnné.

#### <a name="csharp_style_inlined_variable_declaration"></a>styl\_csharp\_\_vložený variable_declaration

|||
|-|-|
| **Název pravidla** | csharp_style_inlined_variable_declaration |
| **ID pravidla** | IDE0018 |
| **Použitelné jazyky** | C# 7.0+ |
| **Hodnoty** | `true`- `out` Preferovat proměnné, které mají být deklarovány v seznamu argumentů volání metody, pokud je to možné<br /><br />`false`- `out` Preferují proměnné, které mají být deklarovány před voláním metody |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Příklad souboru *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="c-expression-level-preferences"></a>Předvolby na úrovni výrazu C#

Pravidla stylu v této části se týkají předvoleb na úrovni výrazu.

Příklad souboru *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>csharp\_\_preferují jednoduché\_default_expression

Toto pravidlo stylu se týká použití [ `default` literálu pro výchozí výrazy hodnot,](/dotnet/csharp/language-reference/operators/default#default-literal) když kompilátor může odvodit typ výrazu.

|||
|-|-|
| **Název pravidla** | csharp_prefer_simple_default_expression |
| **ID pravidla** | IDE0034 |
| **Použitelné jazyky** | C# 7.1+  |
| **Hodnoty** | `true`- `default` Raději před`default(T)`<br /><br />`false`- `default(T)` Raději před`default` |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>Předvolby kontroly nula jazyka C#

Tato pravidla stylu se `null` týkají syntaxe `throw` kolem `throw` kontroly, včetně použití výrazů nebo příkazů, a zda`?.`chcete provést kontrolu null nebo použít operátor podmíněného slučování ( ) při vyvolání [výrazu lambda](/dotnet/csharp/lambda-expressions).

Příklad souboru *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>csharp\_\_styl throw_expression

|||
|-|-|
| **Název pravidla** | csharp_style_throw_expression |
| **ID pravidla** | IDE0016 |
| **Použitelné jazyky** | C# 7.0+ |
| **Hodnoty** | `true`- Raději `throw` používat výrazy `throw` místo příkazů<br /><br />`false`- Raději `throw` používat příkazy místo výrazů `throw` |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>podmíněný\_\_delegate_call\_stylu csharp

|||
|-|-|
| **Název pravidla** | csharp_style_conditional_delegate_call |
| **ID pravidla** | IDE0041 |
| **Použitelné jazyky** | C# 6.0+  |
| **Hodnoty** | `true`- viz použití operátoru podmíněného`?.`slučování ( ) při vyvolání výrazu lambda namísto provedení nulové kontroly<br /><br />`false`- Raději provést kontrolu null před vyvoláním výrazu lambda namísto použití podmíněného`?.`slučování operátor ( ) |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Předvolby bloku kódu

Toto pravidlo stylu se týká `{ }` použití složených závorek k obklíčení bloků kódu.

Příklad souboru *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharp_prefer_braces"></a>csharp\_\_preferují závorky

|||
|-|-|
| **Název pravidla** | csharp_prefer_braces |
| **ID pravidla** | IDE0011 |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true`- Preferujte skaté návěsy i pro jeden řádek kódu<br /><br />`false`- Preferujte žádné skatérové rovnátka, pokud je povoleno<br /><br />`when_multiline`- Preferujte složené rovnátka na více řádcích |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

### <a name="unused-value-preferences"></a>Předvolby nevyužitých hodnot

Tato pravidla stylu se týkají nepoužívaných výrazů a přiřazení hodnot.

Příklad souboru *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_unused_value_expression_statement_preference = discard_variable:silent
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
```

#### <a name="csharp_style_unused_value_expression_statement_preference"></a>csharp_style_unused_value_expression_statement_preference

|||
|-|-|
| **Název pravidla** | csharp_style_unused_value_expression_statement_preference |
| **ID pravidla** | IDE0058 |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `discard_variable`- Raději přiřadit nepoužitý výraz k [zahození](/dotnet/csharp/discards) <br /><br />`unused_local_variable`- Raději přiřadit nepoužitý výraz k místní proměnné |
| **Výchozí nastavení sady Visual Studio** | `discard_variable:silent` |

Příklady kódu:

```csharp
// Original code:
System.Convert.ToInt32("35");

// After code fix for IDE0058:

// csharp_style_unused_value_expression_statement_preference = discard_variable
_ = System.Convert.ToInt32("35");

// csharp_style_unused_value_expression_statement_preference = unused_local_variable
var unused = Convert.ToInt32("35");
```

#### <a name="csharp_style_unused_value_assignment_preference"></a>csharp_style_unused_value_assignment_preference

|||
|-|-|
| **Název pravidla** | csharp_style_unused_value_assignment_preference |
| **ID pravidla** | IDE0059 |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `discard_variable`- Raději použít [zahození](/dotnet/csharp/discards) při přiřazování hodnoty, která není použita<br /><br />`unused_local_variable`- Raději používat místní proměnnou při přiřazování hodnoty, která se nepoužívá |
| **Výchozí nastavení sady Visual Studio** | `discard_variable:suggestion` |

Příklady kódu:

```csharp
// csharp_style_unused_value_assignment_preference = discard_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    _ = wordCount.TryGetValue(searchWord, out var count);
    return count;
}

// csharp_style_unused_value_assignment_preference = unused_local_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    var unused = wordCount.TryGetValue(searchWord, out var count);
    return count;
}
```

### <a name="index-and-range-preferences"></a>Index a předvolby rozsahu

Tato pravidla stylu se týkají použití operátorů indexu a rozsahu, které jsou k dispozici v c# 8.0 a novější.

Příklad souboru *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>csharp\_\_styl\_preferují index_operator

|||
|-|-|
| **Název pravidla** | csharp_style_prefer_index_operator |
| **ID pravidla** | IDE0056 |
| **Použitelné jazyky** | C# 8.0+ |
| **Hodnoty** | `true`- Raději použít `^` operátor při výpočtu indexu od konce kolekce<br /><br />`false`- Nechcete použít operátor `^` při výpočtu indexu od konce kolekce |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_prefer_index_operator = true
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[^1];

// csharp_style_prefer_index_operator = false
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[names.Length - 1];
```

#### <a name="csharp_style_prefer_range_operator"></a>csharp\_\_styl\_preferují range_operator

|||
|-|-|
| **Název pravidla** | csharp_style_prefer_range_operator |
| **ID pravidla** | IDE0057 |
| **Použitelné jazyky** | C# 8.0+ |
| **Hodnoty** | `true`- Raději používat operátor `..` rozsahu při extrahování "plátek" kolekce<br /><br />`false`- Nedávají přednost použití operátoru `..` rozsahu při extrahování "plátek" kolekce |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_prefer_range_operator = true
string sentence = "the quick brown fox";
var sub = sentence[0..^4];

// csharp_style_prefer_range_operator = false
string sentence = "the quick brown fox";
var sub = sentence.Substring(0, sentence.Length - 4);
```

### <a name="miscellaneous-preferences"></a>Různé preference

Tato část obsahuje různá pravidla stylu.

Příklad souboru *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_using_directive_placement = outside_namespace:silent
csharp_prefer_static_local_function = true:suggestion
csharp_prefer_simple_using_statement = true:suggestion
csharp_style_prefer_switch_expression = true:suggestion
```

#### <a name="csharp_style_deconstructed_variable_declaration"></a>csharp\_\_styl deconstructed\_variable_declaration

|||
|-|-|
| **Název pravidla** | csharp_style_deconstructed_variable_declaration |
| **ID pravidla** | IDE0042 |
| **Použitelné jazyky** | C# 7.0+ |
| **Hodnoty** | `true`- Preferujte dekonstruované variabilní prohlášení<br /><br />`false`- Nepreferujte dekonstrukci v variabilních deklaracích |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

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

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>csharp\_\_styl\_\_vzor\_místní přes anonymous_function

Počínaje c# 7.0, C# podporuje [místní funkce](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Místní funkce jsou soukromé metody typu, které jsou vnořeny v jiném členu.

|||
|-|-|
| **Název pravidla** | csharp_style_pattern_local_over_anonymous_function |
| **ID pravidla** | IDE0039 |
| **Použitelné jazyky** | C# 7.0+ |
| **Hodnoty** | `true`- Preferovat místní funkce před anonymními funkcemi<br /><br />`false`- Preferovat anonymní funkce před místními funkcemi |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

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

#### <a name="csharp_using_directive_placement"></a>csharp\_\_pomocí directive_placement

|||
|-|-|
| **Název pravidla** | csharp_using_directive_placement |
| **ID pravidla** | IDE0065 |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `outside_namespace`- `using` Preferovat směrnice, které mají být umístěny mimo obor názvů<br /><br />`inside_namespace`- `using` Preferují směrnice, které mají být umístěny uvnitř oboru názvů |
| **Výchozí nastavení sady Visual Studio** | `outside_namespace:silent` |

Příklady kódu:

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{
    ...
}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
    ...
}
```

#### <a name="csharp_prefer_static_local_function"></a>csharp\_\_preferují statické\_local_function

|||
|-|-|
| **Název pravidla** | csharp_prefer_static_local_function |
| **ID pravidla** | IDE0062 |
| **Použitelné jazyky** | C# 8.0+ |
| **Hodnoty** | `true`- Preferují označení místních funkcí`static`<br /><br />`false`- Nepreferujte označení místních funkcí`static` |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_prefer_static_local_function = true
void M()
{
    Hello();
    static void Hello()
    {
        Console.WriteLine("Hello");
    }
}

// csharp_prefer_static_local_function = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

#### <a name="csharp_prefer_simple_using_statement"></a>csharp\_\_preferují jednoduché\_using_statement

|||
|-|-|
| **Název pravidla** | csharp_prefer_simple_using_statement |
| **ID pravidla** | IDE0063 |
| **Použitelné jazyky** | C# 8.0+ |
| **Hodnoty** | `true`- Raději používat *jednoduchý* `using` příkaz<br /><br />`false`- Nedávají temene používat *jednoduché* `using` prohlášení |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>csharp\_\_styl\_preferují switch_expression

|||
|-|-|
| **Název pravidla** | csharp_style_prefer_switch_expression |
| **ID pravidla** | IDE0066 |
| **Použitelné jazyky** | C# 8.0+ |
| **Hodnoty** | `true`- Raději používat `switch` výraz (zavedens C# 8.0)<br /><br />`false`- Raději používat [příkaz switch](/dotnet/csharp/language-reference/keywords/switch) |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Zavedená verze** |  Visual Studio 2019 verze 16.2  |

Příklady kódu:

```csharp
// csharp_style_prefer_switch_expression = true
return x switch
{
    1 => 1 * 1,
    2 => 2 * 2,
    _ => 0,
};

// csharp_style_prefer_switch_expression = false
switch (x)
{
    case 1:
        return 1 * 1;
    case 2:
        return 2 * 2;
    default:
        return 0;
}
```

## <a name="see-also"></a>Viz také

- [Konvence formátování](editorconfig-formatting-conventions.md)
- [Zásady vytváření názvů](editorconfig-naming-conventions.md)
- [Nastavení konvence kódování .NET pro EditorConfig](editorconfig-code-style-settings-reference.md)
