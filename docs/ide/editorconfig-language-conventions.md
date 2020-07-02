---
title: Jazykové konvence rozhraní .NET pro EditorConfig
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
ms.openlocfilehash: 3fa32e6155959df6e665a807af3b364923ba3f54
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533455"
---
# <a name="language-conventions"></a>Konvence jazyka

Jazykové konvence pro EditorConfig v aplikaci Visual Studio spadají do dvou kategorií: ty, které se vztahují na Visual Basic a C# a ty, které jsou specifické pro jazyk C#. Jazykové konvence mají vliv na to, jak se používají různé aspekty programovacího jazyka, například modifikátory a závorky.

> [!TIP]
> - Chcete-li zobrazit příklady kódu v upřednostňovaném programovacím jazyce, vyberte jej pomocí nástroje pro výběr jazyka v pravém horním rohu okna prohlížeče.
>
>   ![Ovládací prvek pro výběr jazyka kódu](media/code-language-picker.png)
>
> - Pomocí odkazu **v tomto článku** můžete přejít na jiné části stránky.

## <a name="rule-format"></a>Formát pravidla

Pravidla pro jazykové konvence mají následující obecný formát:

`option_name = value:severity`

Pro každou jazykovou konvenci zadáte hodnotu, která definuje, kdy nebo kdy chcete styl preferovat. Mnoho pravidel přijímá hodnotu `true` (Tento styl upřednostňuje) nebo `false` (nepreferovat tento styl). Jiná pravidla akceptují hodnoty, jako například `when_on_single_line` nebo `never` . Druhá část pravidla určuje [závažnost](#severity-levels).

::: moniker range=">=vs-2019"

> [!NOTE]
> Vzhledem k tomu, že jsou jazykové konvence vynutily analyzátory, můžete také nastavit jejich závažnost pomocí výchozí syntaxe konfigurace pro analyzátory. Syntaxe má formu `dotnet_diagnostic.<rule ID>.severity = <severity>` , například `dotnet_diagnostic.IDE0040.severity = silent` . Další informace najdete v tématu [nastavení závažnosti pravidla v souboru EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file).

::: moniker-end

## <a name="severity-levels"></a>Úrovně závažnosti

Závažnost jazykové konvence určuje úroveň, na které se má tento styl vyhovět. V následující tabulce jsou uvedeny možné hodnoty závažnosti a jejich důsledky:

Severity | Efekt
:------- | ------
`error` | Při porušení tohoto pravidla stylu zobrazit chybu kompilátoru.
`warning` | Při porušení tohoto pravidla stylu zobrazit upozornění kompilátoru.
`suggestion` | Když je toto pravidlo stylu porušeno, zobrazte ho uživateli jako návrh. Návrhy se zobrazí jako tři šedé tečky pod prvními dvěma znaky.
`silent` | Nezobrazovat uživateli žádné údaje, pokud je toto pravidlo porušeno. Funkce pro generování kódu generují kód v tomto stylu, ale. Pravidla se `silent` závažností se účastní vyčištění a zobrazují se v nabídce **rychlé akce a refaktoringy** .
`none` | Nezobrazovat uživateli žádné údaje, pokud je toto pravidlo porušeno. Funkce pro generování kódu generují kód v tomto stylu, ale. Pravidla se `none` závažností se nikdy neobjevují v nabídce **rychlé akce a refaktoringu** . Ve většině případů se to považuje za "zakázané" nebo "ignorované".

::: moniker range=">=vs-2019"

## <a name="automatically-configure-code-styles"></a>Automaticky konfigurovat styly kódu

Počínaje verzí Visual Studio 2019 verze 16,3 můžete nakonfigurovat pravidla stylu kódu z nabídky návrhy [rychlých akcí](quick-actions.md) poté, co dojde k porušení stylu.

Změna konvence stylu kódu:

1. Najeďte myší na vlnovkou v editoru a pak otevřete nabídku žárovky, která se zobrazí. Vyberte možnost **Konfigurovat nebo potlačit problémy**  >  **Konfigurovat \<rule ID> styl kódu**.

   ![Konfigurace stylu kódu z nabídky světlé žárovky v aplikaci Visual Studio](media/vs-2019/configure-code-style.png)

2. Odtud vyberte jednu z možností stylu kódu.

   ![Konfigurovat nastavení stylu kódu](media/vs-2019/configure-code-style-setting.png)

   Visual Studio přidá nebo upraví konfigurační nastavení v souboru EditorConfig, jak je znázorněno v poli Náhled.

Chcete-li změnit závažnost porušení stylu kódu, postupujte podle stejných kroků, ale vyberte možnost **Konfigurovat \<rule ID> závažnost** namísto **konfigurace \<rule ID> stylu kódu**. Další informace najdete v tématu [automatické konfigurace závažnosti pravidla](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity).

::: moniker-end

## <a name="net-code-style-settings"></a>Nastavení stylu kódu .NET

Pravidla stylu v této části platí pro C# i Visual Basic.

- [Kvalifikátory "This." a "já"](#this-and-me)
  - \_ \_ for_field kvalifikace stylu \_ dotnet
  - \_ \_ for_property kvalifikace stylu \_ dotnet
  - \_ \_ for_method kvalifikace stylu \_ dotnet
  - \_ \_ for_event kvalifikace stylu \_ dotnet
- [Klíčová slova jazyka namísto názvů typů rozhraní pro odkazy na typy](#language-keywords)
  - \_předdefinovaný \_ Typ stylu dotnet \_ \_ pro lokální hodnoty \_ \_ parameters_members
  - \_předdefinovaný \_ Typ stylu dotnet \_ \_ pro \_ member_access
- [Předvolby modifikátoru](#normalize-modifiers)
  - \_styl dotnet \_ vyžaduje \_ accessibility_modifiers.
  - \_ \_ preferovaný modifier_order jazyka Visual Basic \_
  - \_ \_ pole jen pro čtení stylu dotnet \_
- [Předvolby závorek](#parentheses-preferences)
  - \_ \_ kulaté závorky stylu dotnet \_ v \_ aritmetických \_ binárních \_ operátorech
  - \_ \_ \_ v \_ jiných \_ binárních \_ operátorech se ve stylu dotnet naplní závorky.
  - \_ \_ kulaté závorky stylu dotnet \_ v \_ jiných \_ operátorech
  - \_ \_ kulaté závorky stylu dotnet \_ v \_ relačních \_ binárních \_ operátorech
- [Předvolby na úrovni výrazu](#expression-level-preferences)
  - \_object_initializer stylu \_ dotnet
  - \_collection_initializer stylu \_ dotnet
  - typ dotnet – \_ \_ explicitní \_ tuple_names
  - \_styl dotnet \_ preferovat \_ odvozený \_ tuple_names
  - \_styl dotnet \_ preferovat \_ odvození \_ anonymního \_ typu \_ member_names
  - \_styl dotnet \_ preferovat \_ Automatické \_ vlastnosti
  - styl dotnet – \_ \_ preferovat \_ podmíněný \_ výraz \_ nad \_ přiřazením
  - styl dotnet – \_ \_ preferovat \_ podmíněný \_ výraz při \_ \_ návratu
  - \_styl dotnet \_ preferovat \_ složené \_ přiřazení
- [Předvolby kontroly "null"](#null-checking-preferences)
  - \_coalesce_expression stylu \_ dotnet
  - \_null_propagation stylu \_ dotnet
  - \_styl dotnet \_ preferovat \_ je \_ hodnota \_ null \_ kontroly \_ nad \_ referenční \_ metodou rovnosti.

### <a name="this-and-me-qualifiers"></a><a name="this-and-me"></a>"This." a "já". kvalifikátory

Toto pravidlo stylu lze použít pro pole, vlastnosti, metody nebo události. Hodnota **true** znamená, že se symbol kódu bude předcházet `this.` v jazyce C# nebo `Me.` v Visual Basic. Hodnota **false** znamená, že by element Code _neměl_ být s `this.` nebo `Me.` .

Tato pravidla by se mohla objevit v souboru *. editorconfig* následujícím způsobem:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>\_ \_ for_field kvalifikace stylu \_ dotnet

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_qualification_for_field |
| **ID pravidla** | IDE0003 a IDE0009 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`-Preferovat pole, která se mají předcházet `this.` v jazyce C# nebo `Me.` v Visual Basic<br /><br />`false`– Preferovat pole, která _nemají_ být uvozena `this.` nebo`Me.` |
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

#### <a name="dotnet_style_qualification_for_property"></a>\_ \_ for_property kvalifikace stylu \_ dotnet

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_qualification_for_property |
| **ID pravidla** | IDE0003 a IDE0009 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`-Preferovat vlastnosti, které mají být `this.` v jazyce C# nebo `Me.` v Visual Basic<br /><br />`false`-Upřednostnit vlastnosti, které _nemají_ být uvozeny `this.` nebo`Me.` |
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

#### <a name="dotnet_style_qualification_for_method"></a>\_ \_ for_method kvalifikace stylu \_ dotnet

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_qualification_for_method |
| **ID pravidla** | IDE0003 a IDE0009 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`-Preferovat metody, které mají být `this.` v jazyce C# nebo `Me.` v Visual Basic.<br /><br />`false`-Preferovat metody, které _nemají_ být uvozeny `this.` nebo `Me.` . |
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

#### <a name="dotnet_style_qualification_for_event"></a>\_ \_ for_event kvalifikace stylu \_ dotnet

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_qualification_for_event |
| **ID pravidla** | IDE0003 a IDE0009 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`-Preferovat události, které mají být `this.` v jazyce C# nebo `Me.` v Visual Basic.<br /><br />`false`-Preferovat události, které _nemusejí_ být uvozeny `this.` nebo `Me.` . |
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

### <a name="language-keywords-instead-of-framework-type-names-for-type-references"></a><a name="language-keywords"></a>Klíčová slova jazyka namísto názvů typů rozhraní pro odkazy na typy

Toto pravidlo stylu lze použít pro lokální proměnné, parametry metody a členy třídy nebo jako samostatné pravidlo pro typ výrazů přístupu členů. Hodnota **true** znamená preferovat klíčové slovo jazyka (například `int` nebo `Integer` ) namísto názvu typu (například `Int32` ) pro typy, které mají klíčové slovo reprezentovat. Hodnota **false** znamená raději název typu místo klíčového slova Language.

Tato pravidla by se mohla objevit v souboru *. editorconfig* následujícím způsobem:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>\_předdefinovaný \_ Typ stylu dotnet \_ \_ pro lokální hodnoty \_ \_ parameters_members

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_predefined_type_for_locals_parameters_members |
| **ID pravidla** | IDE0012 a IDE0014 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`– Preferovat klíčové slovo jazyka pro místní proměnné, parametry metody a členy třídy místo názvu typu, pro typy, které mají klíčové slovo k reprezentování<br /><br />`false`– Raději zadejte název typu pro lokální proměnné, parametry metody a členy třídy místo klíčového slova Language. |
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

#### <a name="dotnet_style_predefined_type_for_member_access"></a>\_předdefinovaný \_ Typ stylu dotnet \_ \_ pro \_ member_access

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_predefined_type_for_member_access |
| **ID pravidla** | IDE0013 a IDE0015 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`– Preferovat klíčové slovo jazyka pro výrazy přístupu členů namísto názvu typu, pro typy, které mají klíčové slovo, které je reprezentovat<br /><br />`false`– Raději jako název typu pro výrazy přístupu členů místo klíčového slova Language |
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

Pravidla stylu v této části se týkají předvoleb modifikátoru, včetně vyžadování modifikátorů přístupnosti, určení pořadí řazení požadovaného modifikátoru a vyžadování modifikátoru jen pro čtení.

Tato pravidla by se mohla objevit v souboru *. editorconfig* následujícím způsobem:

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

#### <a name="dotnet_style_require_accessibility_modifiers"></a>\_styl dotnet \_ vyžaduje \_ accessibility_modifiers.

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_require_accessibility_modifiers |
| **ID pravidla** | IDE0040 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always`– Preferovat Modifikátory dostupnosti, které se mají zadat.<br /><br />`for_non_interface_members`– Upřednostnit Modifikátory dostupnosti, které mají být deklarovány s výjimkou členů veřejných rozhraní. (To je stejné jako **Always** a bylo přidáno pro budoucí kontrolu pravopisu, pokud jazyk C# přidá metody výchozích rozhraní.)<br /><br />`never`– Nepreferovat Modifikátory dostupnosti, které se mají zadat<br /><br />`omit_if_default`– Upřednostnit Modifikátory dostupnosti, které mají být zadány s výjimkou případů, kdy jsou výchozím modifikátorem. |
| **Výchozí nastavení sady Visual Studio** | `for_non_interface_members:silent` |
| **Představená verze** | Visual Studio 2017 verze 15.5 |

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

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_preferred_modifier_order |
| **ID pravidla** | IDE0036 |
| **Příslušné jazyky** | C# |
| **Hodnoty** | Jeden nebo více modifikátorů jazyka C#, například `public` , `private` a`protected` |
| **Výchozí nastavení sady Visual Studio** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Představená verze** | Visual Studio 2017 verze 15.5 |

- Pokud je toto pravidlo nastaveno na seznam modifikátorů, preferovat zadané řazení.
- Pokud je toto pravidlo vynecháno ze souboru, nedoporučujeme pořadí modifikátorů.

Příklady kódu:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

#### <a name="visual_basic_preferred_modifier_order"></a>visual_basic_preferred_modifier_order

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | visual_basic_preferred_modifier_order |
| **ID pravidla** | IDE0036 |
| **Příslušné jazyky** | Visual Basic |
| **Hodnoty** | Jeden nebo více modifikátorů Visual Basic, například `Partial` , `Private` , a`Public` |
| **Výchozí nastavení sady Visual Studio** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Představená verze** | Visual Studio 2017 verze 15.5 |

- Pokud je toto pravidlo nastaveno na seznam modifikátorů, preferovat zadané řazení.
- Pokud je toto pravidlo vynecháno ze souboru, nedoporučujeme pořadí modifikátorů.

Příklady kódu:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="visual_basic_style_unused_value_expression_statement_preference"></a>visual_basic_style_unused_value_expression_statement_preference

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | visual_basic_style_unused_value_expression_statement_preference |
| **ID pravidla** | IDE0058 |
| **Příslušné jazyky** | Visual Basic |
| **Hodnoty** | `unused_local_variable:silent` |
| **Výchozí nastavení sady Visual Studio** | `unused_local_variable:silent` |

Příklady kódu:

```vb
' visual_basic_style_unused_value_expression_statement_preference = unused_local_variable:silent

Dim unused = Computation()
```

#### <a name="visual_basic_style_unused_value_assignment_preference"></a>visual_basic_style_unused_value_assignment_preference

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | visual_basic_style_unused_value_assignment_preference |
| **ID pravidla** | IDE0059 |
| **Příslušné jazyky** | Visual Basic |
| **Hodnoty** | `unused_local_variable:silent` |
| **Výchozí nastavení sady Visual Studio** | `unused_local_variable:silent` |

Příklady kódu:

```vb
' visual_basic_style_unused_value_assignment_preference = unused_local_variable:suggestion

Dim unused = Computation()
Dim x = 1;
```

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_readonly_field |
| **ID pravidla** | IDE0044 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`– Preferovat, že pole by měla být označena pomocí `readonly` (C#) nebo `ReadOnly` (Visual Basic), pokud jsou pouze přiřazena vložená nebo uvnitř konstruktoru<br /><br />`false`-Neurčovat, zda mají být pole označeny hodnotou `readonly` (C#) nebo `ReadOnly` (Visual Basic) |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2017 verze 15.7 |

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

Pravidla stylu v této části se týkají předvoleb závorek, včetně použití závorek pro aritmetické, relační a další binární operátory.

Tato pravidla by se mohla objevit v souboru *. editorconfig* následujícím způsobem:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>\_ \_ kulaté závorky stylu dotnet \_ v \_ aritmetických \_ binary_operators

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **ID pravidla** | IDE0047 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always_for_clarity`– Preferovat kulaté závorky pro objasnění aritmetického operátoru ( `*` , `/` ,, `%` `+` , `-` , `<<` , `>>` , `&` , `^` , `|` ) priority<br /><br />`never_if_unnecessary`– Raději nepoužívejte závorky, pokud je přednost aritmetického operátoru ( `*` , `/` ,, `%` `+` , `-` , `<<` , `>>` , `&` , `^` , `|` ). |
| **Výchozí nastavení sady Visual Studio** | `always_for_clarity:silent` |
| **Představená verze** | Visual Studio 2017 verze 15,8 |

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

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>\_ \_ kulaté závorky stylu dotnet \_ v \_ relačních \_ binary_operators

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_parentheses_in_relational_binary_operators |
| **ID pravidla** | IDE0047 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always_for_clarity`– Upřednostnit kulaté závorky k objasnění relačních operátorů ( `>` , `<` ,, `<=` `>=` , `is` , `as` , `==` , `!=` ) priority<br /><br />`never_if_unnecessary`– Nedoporučuje se závorky, když relační operátor ( `>` , `<` , `<=` , `>=` , `is` , `as` , `==` , `!=` ) je zřejmý. |
| **Výchozí nastavení sady Visual Studio** | `always_for_clarity:silent` |
| **Představená verze** | Visual Studio 2017 verze 15,8 |

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

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>\_ \_ kulaté závorky stylu dotnet \_ v \_ jiných \_ binary_operators

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_parentheses_in_other_binary_operators |
| **ID pravidla** | IDE0047 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always_for_clarity`– Preferovat kulaté závorky pro vysvětlení jiné binární operátory ( `&&` , `||` , `??` ) priority<br /><br />`never_if_unnecessary`– Raději nepoužívejte závorky, pokud je jiná priorita binárního operátoru ( `&&` , `||` , `??` ) zřejmá. |
| **Výchozí nastavení sady Visual Studio** | `always_for_clarity:silent` |
| **Představená verze** | Visual Studio 2017 verze 15,8 |

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

#### <a name="dotnet_style_parentheses_in_other_operators"></a>\_ \_ \_ v other_operators se závorky ve stylu dotnet \_

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_parentheses_in_other_operators |
| **ID pravidla** | IDE0047 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always_for_clarity`– Preferovat kulaté závorky k objasnění priority operátoru<br /><br />`never_if_unnecessary`-Preferovat, pokud je přednost operátoru, nemusíte mít závorky |
| **Výchozí nastavení sady Visual Studio** | `never_if_unnecessary:silent` |
| **Představená verze** | Visual Studio 2017 verze 15,8 |

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

Pravidla stylu v této části se týkají předvoleb na úrovni výrazu, včetně použití inicializátorů objektů, inicializátorů kolekcí, explicitních nebo odvozených názvů řazených kolekcí členů a odvozených anonymních typů.

Tato pravidla by se mohla objevit v souboru *. editorconfig* následujícím způsobem:

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

#### <a name="dotnet_style_object_initializer"></a>\_object_initializer stylu \_ dotnet

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_object_initializer |
| **ID pravidla** | IDE0017 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`– Preferovat objekty, které se mají inicializovat pomocí inicializátorů objektů, pokud je to možné<br /><br />`false`-Preferovat objekty, které se *nemají* inicializovat pomocí inicializátorů objektů |
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

#### <a name="dotnet_style_collection_initializer"></a>\_collection_initializer stylu \_ dotnet

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_collection_initializer |
| **ID pravidla** | IDE0028 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`– Preferovat kolekce, které se mají inicializovat pomocí inicializátorů kolekcí, pokud je to možné<br /><br />`false`-Preferovat kolekce, které se *nemají* inicializovat pomocí inicializátorů kolekcí |
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

#### <a name="dotnet_style_explicit_tuple_names"></a>typ dotnet – \_ \_ explicitní \_ tuple_names

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_explicit_tuple_names |
| **ID pravidla** | IDE0033 |
| **Příslušné jazyky** | C# 7.0 + a Visual Basic 15 + |
| **Hodnoty** | `true`-Preferovat názvy řazené kolekce členů k ItemXm vlastnostem<br /><br />`false`– Preferovat vlastnosti ItemX názvů řazených kolekcí členů |
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

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>\_styl dotnet \_ preferovat \_ odvozený \_ tuple_names

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_prefer_inferred_tuple_names |
| **ID pravidla** | IDE0037 |
| **Příslušné jazyky** | C# 7.1 + a Visual Basic 15 + |
| **Hodnoty** | `true`-Preferovat odvozené názvy elementů řazené kolekce členů<br /><br />`false`-Preferovat explicitní názvy elementů řazené kolekce členů |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2017 verze 15.6 |

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

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>\_styl dotnet \_ preferovat \_ odvození \_ anonymního \_ typu \_ member_names

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **ID pravidla** | IDE0037 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`-Preferovat odvozené názvy členů anonymního typu<br /><br />`false`-Preferovat explicitní názvy členů anonymního typu |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2017 verze 15.6 |

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

#### <a name="dotnet_style_prefer_auto_properties"></a>\_styl dotnet \_ preferovat \_ Automatické \_ vlastnosti

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_prefer_auto_properties |
| **ID pravidla** | IDE0032 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`– Preferovat vlastnosti autoproperties přes vlastnosti s privátními zálohovanými poli<br /><br />`false`-Preferovat vlastnosti pomocí soukromých zálohovacích polí přes autoproperties |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2017 verze 15.7 |

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

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>\_styl dotnet \_ preferovat \_ je \_ hodnota \_ null \_ kontroly \_ nad \_ referenční \_ metodou rovnosti.

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **ID pravidla** | IDE0041 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`– Raději použijte kontrolu null se porovnáváním vzorů.`object.ReferenceEquals`<br /><br />`false`– Preferovat pro `object.ReferenceEquals` kontrolu s hodnotou null se porovnáváním vzorů |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2017 verze 15.7 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>\_styl dotnet \_ preferovat \_ podmíněný \_ výraz \_ over_assignment

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_prefer_conditional_expression_over_assignment |
| **ID pravidla** | IDE0045 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`-Upřednostnit přiřazení s ternárním podmíněným příkazem if-else<br /><br />`false`– Preferovat přiřazení pomocí příkazu if-else přes Ternární podmíněný |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2017 verze 15,8 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>\_styl dotnet \_ preferovat \_ podmíněný \_ výraz \_ over_return

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_prefer_conditional_expression_over_return |
| **ID pravidla** | IDE0046 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`-Preferovat návratové příkazy pro použití ternárního podmíněného příkazu if-else<br /><br />`false`-Preferovat návratové příkazy pro použití příkazu if-else nad Ternární podmínkou |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2017 verze 15,8 |

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

#### <a name="dotnet_style_prefer_compound_assignment"></a>\_styl dotnet \_ preferovat \_ složené \_ přiřazení

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_prefer_compound_assignment |
| **ID pravidla** | IDE0054 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`-Preferovat výrazy [složeného přiřazení](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment)<br /><br />`false`– Nepreferovat výrazy složeného přiřazení |
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

### <a name="null-checking-preferences"></a>Předvolby pro kontrolu hodnoty null

Pravidla stylu v této části se týkají předvoleb pro kontrolu hodnoty null.

Tato pravidla by se mohla objevit v souboru *. editorconfig* následujícím způsobem:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
```

#### <a name="dotnet_style_coalesce_expression"></a>\_coalesce_expression stylu \_ dotnet

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_coalesce_expression |
| **ID pravidla** | IDE0029 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true`– Upřednostnit hodnoty null slučovacích výrazů pro kontrolu ternárních operátorů<br /><br />`false`-Upřednostnit Ternární operátor zaškrtnutí na hodnoty null slučovacích výrazů |
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

#### <a name="dotnet_style_null_propagation"></a>\_null_propagation stylu \_ dotnet

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_null_propagation |
| **ID pravidla** | IDE0031 |
| **Příslušné jazyky** | C# 6.0 + a Visual Basic 14 + |
| **Hodnoty** | `true`– Raději použijte operátor s hodnotou null, pokud je to možné<br /><br />`false`– Raději použijte kontrolu Ternární hodnoty null, pokud je to možné |
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

### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>\_styl dotnet \_ preferovat \_ je \_ hodnota \_ null \_ kontroly \_ nad \_ referenční \_ metodou rovnosti.

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **ID pravidla** | IDE0041 |
| **Příslušné jazyky** | C# 6.0 + a Visual Basic 14 + |
| **Hodnoty** | `true`– Preferovat, je hodnota null kontroly nad referenční metodou rovnosti<br /><br />`false`-Upřednostnit metodu rovnosti referencí nad hodnotou je vrácení hodnoty null |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

## <a name="net-code-quality-settings"></a>Nastavení kvality kódu .NET

Pravidla kvality v této části se vztahují na kód C# i Visual Basic. Slouží ke konfiguraci analyzátorů kódu, které jsou integrovány do integrovaného vývojového prostředí (IDE) sady Visual Studio. Informace o konfiguraci analyzátorů FxCop pomocí souboru EditorConfig najdete v tématu [Konfigurace analyzátorů FxCop](../code-quality/configure-fxcop-analyzers.md).

- [Předvolby parametrů](#parameter-preferences)
  - \_nepoužívané \_ \_ parametry kvality kódu dotnet \_

### <a name="parameter-preferences"></a>Předvolby parametrů

Pravidla kvality v této části se týkají parametrů metod.

Tato pravidla by se mohla objevit v souboru *. editorconfig* následujícím způsobem:

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>\_nepoužívané \_ \_ parametry kvality kódu dotnet \_

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_code_quality_unused_parameters |
| **ID pravidla** | IDE0060 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `all`-Flag metody s jakýmkoli přístupným příznakem, který obsahuje nepoužívané parametry<br /><br />`non_public`– Označí jenom neveřejné metody, které obsahují nepoužité parametry. |
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

## <a name="c-code-style-settings"></a>Nastavení stylu kódu C#

Pravidla stylu v této části se vztahují pouze na C#.

- [Implicitní a explicitní typy](#implicit-and-explicit-types)
  - \_var Style \_ CSharp \_ pro \_ sestavené \_ in_types
  - csharpovat \_ \_ var \_ při \_ typu \_ is_apparent
  - \_var_elsewhere stylu \_ CSharp
- [Členové tvoření výrazy](#expression-bodied-members)
  - \_ \_ bodied_methods výrazu stylu \_ CSharp
  - \_ \_ bodied_constructors výrazu stylu \_ CSharp
  - \_ \_ bodied_operators výrazu stylu \_ CSharp
  - \_ \_ bodied_properties výrazu stylu \_ CSharp
  - \_ \_ bodied_indexers výrazu stylu \_ CSharp
  - \_ \_ bodied_accessors výrazu stylu \_ CSharp
  - \_ \_ bodied_lambdas výrazu stylu \_ CSharp
  - CSharp \_ stylu \_ výrazu \_ těle \_ local_functions
- [Porovnávání vzorů](#pattern-matching)
  - CSharp \_ \_ \_ porovnávání vzorů \_ ve stylu \_ je \_ s \_ cast_check
  - CSharp \_ \_ porovnávání vzorů stylu \_ \_ \_ jako \_ s \_ null_check
- [Vložené deklarace proměnných](#inlined-variable-declarations)
  - \_styl CSharp \_ vložen \_ variable_declaration
- [Předvolby na úrovni výrazu](#c-expression-level-preferences)
  - CSharp \_ preferovat \_ jednoduché \_ default_expression
- [Předvolby kontroly "null"](#c-null-checking-preferences)
  - \_throw_expression stylu \_ CSharp
  - \_ \_ podmíněné delegate_call ve stylu CSharp \_
- [Předvolby modifikátoru](#normalize-modifiers)
  - CSharp \_ preferované \_ modifier_order
- [Předvolby bloku kódu](#code-block-preferences)
  - CSharp \_ prefer_braces
- [Předvolby nepoužité hodnoty](#unused-value-preferences)
  - CSharp \_ \_ \_ \_ statement_preference výrazu hodnoty s nepoužitým stylem \_
  - CSharp \_ \_ nepoužité \_ assignment_preference hodnoty stylu \_
- [Předvolby indexu a rozsahu](#index-and-range-preferences)
  - CSharp \_ styl \_ preferovat \_ index_operator
  - CSharp \_ styl \_ preferovat \_ range_operator
- [Různé předvolby](#miscellaneous-preferences)
  - \_ \_ variable_declaration Dekonstruovaný styl \_ CSharp
  - CSharp \_ \_ vzor stylu \_ místní \_ po \_ anonymous_function
  - CSharp \_ používající \_ \_ umístění direktiv
  - CSharp \_ preferovat \_ statické \_ local_function
  - CSharp \_ preferovat \_ jednoduché \_ using_statement
  - CSharp \_ styl \_ preferovat \_ switch_expression

### <a name="implicit-and-explicit-types"></a>Implicitní a explicitní typy

Pravidla stylu v této části se týkají použití klíčového slova [var](/dotnet/csharp/language-reference/keywords/var) a explicitního typu v deklaraci proměnné. Toto pravidlo lze použít samostatně pro předdefinované typy, pokud je typ zřejmý a jinde.

Příklad souboru *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharp_style_var_for_built_in_types"></a>\_var Style \_ CSharp \_ pro \_ sestavené \_ in_types

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_var_for_built_in_types |
| **ID pravidla** | IDE0007 a IDE0008 |
| **Příslušné jazyky** | C#  |
| **Hodnoty** | `true`-Preferovat `var` se používá k deklaraci proměnných s integrovanými systémovými typy, jako je například`int`<br /><br />`false`-Preferovat explicitní typ `var` pro deklaraci proměnných s integrovanými systémovými typy, jako například`int` |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>csharpovat \_ \_ var \_ při \_ typu \_ is_apparent

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_var_when_type_is_apparent |
| **ID pravidla** | IDE0007 a IDE0008 |
| **Příslušné jazyky** | C#  |
| **Hodnoty** | `true`– Preferovat `var` , když je typ již uveden na pravé straně výrazu deklarace<br /><br />`false`-Preferovat explicitní typ, `var` Pokud je již tento typ uveden na pravé straně výrazu deklarace |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>\_var_elsewhere stylu \_ CSharp

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_var_elsewhere |
| **ID pravidla** | IDE0007 a IDE0008 |
| **Příslušné jazyky** | C#  |
| **Hodnoty** | `true`-Preferovat `var` přes explicitní typ ve všech případech, pokud není přepsán jiným pravidlem stylu kódu.<br /><br />`false`-Preferovat explicitní typ `var` ve všech případech, pokud není přepsán jiným pravidlem stylu kódu |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>Členové tvoření výrazy

Pravidla stylu v této části se týkají použití [členů Expression-těle](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) , když se logika skládá z jediného výrazu. Toto pravidlo lze použít pro metody, konstruktory, operátory, vlastnosti, indexery a přistupující objekty.

Příklad souboru *. editorconfig* :

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

#### <a name="csharp_style_expression_bodied_methods"></a>\_ \_ bodied_methods výrazu stylu \_ CSharp

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_methods |
| **ID pravidla** | IDE0022 |
| **Příslušné jazyky** | C# 6.0 +  |
| **Hodnoty** | `true`-Preferovat texty výrazu pro metody<br /><br />`when_on_single_line`– Preferovat texty výrazu pro metody, když budou představovat jeden řádek<br /><br />`false`-Preferovat blokové texty pro metody |
| **Výchozí nastavení sady Visual Studio** | `false:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>\_ \_ bodied_constructors výrazu stylu \_ CSharp

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_constructors |
| **ID pravidla** | IDE0021 |
| **Příslušné jazyky** | C# 7.0 + |
| **Hodnoty** | `true`-Preferovat texty výrazu pro konstruktory<br /><br />`when_on_single_line`– Preferovat texty výrazu pro konstruktory, když budou představovat jeden řádek<br /><br />`false`-Preferovat blokové texty pro konstruktory |
| **Výchozí nastavení sady Visual Studio** | `false:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>\_ \_ bodied_operators výrazu stylu \_ CSharp

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_operators |
| **ID pravidla** | IDE0023 a IDE0024 |
| **Příslušné jazyky** | C# 7.0 + |
| **Hodnoty** | `true`-Preferovat texty výrazu pro operátory<br /><br />`when_on_single_line`– Preferovat texty výrazu pro operátory, když budou být jedním řádkem<br /><br />`false`-Preferovat blokové texty pro operátory |
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

#### <a name="csharp_style_expression_bodied_properties"></a>\_ \_ bodied_properties výrazu stylu \_ CSharp

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_properties |
| **ID pravidla** | IDE0025 |
| **Příslušné jazyky** | C# 7.0 + |
| **Hodnoty** | `true`-Preferovat texty výrazu pro vlastnosti<br /><br />`when_on_single_line`– Preferovat tělo výrazu pro vlastnosti, když budou představovat jeden řádek<br /><br />`false`-Preferovat blokové texty pro vlastnosti |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>\_ \_ bodied_indexers výrazu stylu \_ CSharp

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_indexers |
| **ID pravidla** | IDE0026 |
| **Příslušné jazyky** | C# 7.0 + |
| **Hodnoty** | `true`-Preferovat texty výrazu pro indexery<br /><br />`when_on_single_line`– Preferovat texty výrazu pro indexery, když budou být jedním řádkem<br /><br />`false`-Preferovat blokové texty pro indexery |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>\_ \_ bodied_accessors výrazu stylu \_ CSharp

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_accessors |
| **ID pravidla** | IDE0027 |
| **Příslušné jazyky** | C# 7.0 + |
| **Hodnoty** | `true`-Preferovat texty výrazu pro přistupující objekty<br /><br />`when_on_single_line`– Preferovat texty výrazu pro přistupující objekty, když budou být jedním řádkem<br /><br />`false`-Preferovat blokové texty pro přistupující objekty |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>\_ \_ bodied_lambdas výrazu stylu \_ CSharp

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_lambdas |
| **ID pravidla** | IDE0053 |
| **Hodnoty** | `true`-Preferovat texty výrazu pro výrazy lambda<br /><br />`when_on_single_line`– Preferovat výrazy výrazů pro lambda, pokud budou být jedním řádkem<br /><br />`false`-Preferovat blokové texty pro výrazy lambda |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>CSharp \_ stylu \_ výrazu \_ těle \_ local_functions

Počínaje jazykem C# 7,0 podporuje jazyk C# [místní funkce](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Lokální funkce jsou soukromé metody typu, které jsou vnořené v jiném členu.

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_local_functions |
| **ID pravidla** | IDE0061 |
| **Příslušné jazyky** | C# 7.0 + |
| **Hodnoty** | `true`-Preferovat texty výrazu pro místní funkce<br /><br />`when_on_single_line`– Preferovat tělo výrazu pro místní funkce, když budou to jeden řádek<br /><br />`false`-Preferovat blokové texty pro místní funkce |
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

Pravidla stylu v této části se týkají použití [porovnávání vzorů](/dotnet/csharp/pattern-matching) v jazyce C#.

Příklad souboru *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>CSharp \_ \_ \_ porovnávání vzorů \_ ve stylu \_ je \_ s \_ cast_check

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_pattern_matching_over_is_with_cast_check |
| **ID pravidla** | IDE0020 |
| **Příslušné jazyky** | C# 7.0 + |
| **Hodnoty** | `true`-Preferovat porovnávání vzorů místo `is` výrazů s přetypováními typů<br /><br />`false`-Preferovat `is` výrazy s přetypováními typu místo porovnávání vzorů |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>CSharp \_ \_ porovnávání vzorů stylu \_ \_ \_ jako \_ s \_ null_check

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_pattern_matching_over_as_with_null_check |
| **ID pravidla** | IDE0019 |
| **Příslušné jazyky** | C# 7.0 + |
| **Hodnoty** | `true`-Preferovat porovnávání vzorů místo `as` výrazů s kontrolou null k určení, jestli je něco konkrétního typu<br /><br />`false`-Preferovat `as` výrazy s nulovými kontrolami namísto porovnávání vzorů, abyste zjistili, jestli je něco konkrétního typu |
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

Toto pravidlo stylu se týká, zda `out` jsou proměnné deklarovány jako vložené nebo nikoli. Počínaje jazykem C# 7 můžete [deklarovat proměnnou out v seznamu argumentů volání metody](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), nikoli v deklaraci samostatné proměnné.

#### <a name="csharp_style_inlined_variable_declaration"></a>\_styl CSharp \_ vložen \_ variable_declaration

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_inlined_variable_declaration |
| **ID pravidla** | IDE0018 |
| **Příslušné jazyky** | C# 7.0 + |
| **Hodnoty** | `true`-Preferovat `out` proměnné, které se mají deklarovat jako vložené v seznamu argumentů volání metody, pokud je to možné<br /><br />`false`-Preferovat `out` proměnné, které se mají deklarovat před voláním metody |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Příklad souboru *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="c-expression-level-preferences"></a>Předvolby na úrovni výrazu v C#

Pravidla stylu v této části se týkají předvoleb na úrovni výrazu.

Příklad souboru *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>CSharp \_ preferovat \_ jednoduché \_ default_expression

Toto pravidlo stylu se týká použití [ `default` literálu pro výrazy výchozích hodnot](/dotnet/csharp/language-reference/operators/default#default-literal) , když kompilátor může odvodit typ výrazu.

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_prefer_simple_default_expression |
| **ID pravidla** | IDE0034 |
| **Příslušné jazyky** | C# 7.1 +  |
| **Hodnoty** | `true`– Preferovat `default``default(T)`<br /><br />`false`– Preferovat `default(T)``default` |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>Předvolby pro kontrolu hodnoty null jazyka C#

Tato pravidla stylu se týkají syntaxe `null` při kontrole, včetně použití `throw` výrazů nebo `throw` příkazů a zda má být provedena kontrola s hodnotou null nebo použití operátoru podmíněného sloučení ( `?.` ) při volání [výrazu lambda](/dotnet/csharp/lambda-expressions).

Příklad souboru *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>\_throw_expression stylu \_ CSharp

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_throw_expression |
| **ID pravidla** | IDE0016 |
| **Příslušné jazyky** | C# 7.0 + |
| **Hodnoty** | `true`– Raději `throw` místo příkazů použít výrazy `throw`<br /><br />`false`– Raději `throw` místo výrazů použít příkazy `throw` |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>\_ \_ podmíněné delegate_call ve stylu CSharp \_

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_conditional_delegate_call |
| **ID pravidla** | IDE0041 |
| **Příslušné jazyky** | C# 6.0 +  |
| **Hodnoty** | `true`– `?.` při volání výrazu lambda namísto kontroly hodnoty null se používá operátor podmíněného slučování ().<br /><br />`false`– Před voláním výrazu lambda se doporučuje provést kontrolu null, místo použití operátoru podmíněného slučování (). `?.` |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Předvolby bloku kódu

Toto pravidlo stylu se týká použití složených závorek `{ }` k obklopení bloků kódu.

Příklad souboru *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharp_prefer_braces"></a>CSharp \_ preferovat \_ složené závorky

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_prefer_braces |
| **ID pravidla** | IDE0011 |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true`-Preferovat složené závorky i pro jeden řádek kódu<br /><br />`false`-Preferovat žádné složené závorky, pokud je povoleno<br /><br />`when_multiline`-Preferovat složené závorky na více řádcích |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

### <a name="unused-value-preferences"></a>Předvolby nepoužité hodnoty

Tato pravidla stylu se týkají nepoužitých výrazů a přiřazení hodnot.

Příklad souboru *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_unused_value_expression_statement_preference = discard_variable:silent
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
```

#### <a name="csharp_style_unused_value_expression_statement_preference"></a>csharp_style_unused_value_expression_statement_preference

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_unused_value_expression_statement_preference |
| **ID pravidla** | IDE0058 |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `discard_variable`– Raději přiřaďte nepoužitý výraz k [zahození](/dotnet/csharp/discards) <br /><br />`unused_local_variable`– Raději přiřaďte nepoužitý výraz místní proměnné. |
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

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_unused_value_assignment_preference |
| **ID pravidla** | IDE0059 |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `discard_variable`– Upřednostňuje použití [zahození](/dotnet/csharp/discards) při přiřazení hodnoty, která se nepoužívá.<br /><br />`unused_local_variable`– Raději použijte místní proměnnou při přiřazení hodnoty, která se nepoužívá. |
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

### <a name="index-and-range-preferences"></a>Předvolby indexu a rozsahu

Tato pravidla stylu se týkají použití operátorů index a rozsah, které jsou k dispozici v C# 8,0 a novějších.

Příklad souboru *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>CSharp \_ styl \_ preferovat \_ index_operator

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_prefer_index_operator |
| **ID pravidla** | IDE0056 |
| **Příslušné jazyky** | C# 8.0 + |
| **Hodnoty** | `true`– Raději použít `^` operátor při výpočtu indexu z konce kolekce<br /><br />`false`– Nedoporučuje se použít `^` operátor při výpočtu indexu z konce kolekce. |
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

#### <a name="csharp_style_prefer_range_operator"></a>CSharp \_ styl \_ preferovat \_ range_operator

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_prefer_range_operator |
| **ID pravidla** | IDE0057 |
| **Příslušné jazyky** | C# 8.0 + |
| **Hodnoty** | `true`– Raději použít operátor rozsahu `..` při extrakci "řezu" kolekce<br /><br />`false`– `..` Při extrakci řezu kolekce nedoporučuje používat operátor rozsahu |
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

### <a name="miscellaneous-preferences"></a>Různé předvolby

Tato část obsahuje různá pravidla stylu.

Příklad souboru *. editorconfig* :

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

#### <a name="csharp_style_deconstructed_variable_declaration"></a>\_ \_ variable_declaration Dekonstruovaný styl \_ CSharp

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_deconstructed_variable_declaration |
| **ID pravidla** | IDE0042 |
| **Příslušné jazyky** | C# 7.0 + |
| **Hodnoty** | `true`-Preferovat deklaraci dekonstruovaných proměnných<br /><br />`false`– Nepreferovat dekonstrukci v deklaracích proměnných |
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

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>CSharp \_ \_ vzor stylu \_ místní \_ po \_ anonymous_function

Počínaje jazykem C# 7,0 podporuje jazyk C# [místní funkce](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Lokální funkce jsou soukromé metody typu, které jsou vnořené v jiném členu.

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_pattern_local_over_anonymous_function |
| **ID pravidla** | IDE0039 |
| **Příslušné jazyky** | C# 7.0 + |
| **Hodnoty** | `true`– Upřednostnit místní funkce přes anonymní funkce<br /><br />`false`– Upřednostnit anonymní funkce nad místními funkcemi |
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

#### <a name="csharp_using_directive_placement"></a>CSharp \_ pomocí \_ directive_placement

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_using_directive_placement |
| **ID pravidla** | IDE0065 |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `outside_namespace`-Preferovat `using` direktivy, které mají být umístěny mimo obor názvů<br /><br />`inside_namespace`-Preferovat `using` direktivy, které mají být umístěny uvnitř oboru názvů |
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

#### <a name="csharp_prefer_static_local_function"></a>CSharp \_ preferovat \_ statické \_ local_function

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_prefer_static_local_function |
| **ID pravidla** | IDE0062 |
| **Příslušné jazyky** | C# 8.0 + |
| **Hodnoty** | `true`-Upřednostnit místní funkce, které mají být označeny`static`<br /><br />`false`-Nepreferovat místní funkce, které mají být označeny`static` |
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

#### <a name="csharp_prefer_simple_using_statement"></a>CSharp \_ preferovat \_ jednoduché \_ using_statement

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_prefer_simple_using_statement |
| **ID pravidla** | IDE0063 |
| **Příslušné jazyky** | C# 8.0 + |
| **Hodnoty** | `true`– Preferovat použití *jednoduchého* `using` příkazu<br /><br />`false`– Nedoporučujeme používat *jednoduchý* `using` příkaz. |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>CSharp \_ styl \_ preferovat \_ switch_expression

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_style_prefer_switch_expression |
| **ID pravidla** | IDE0066 |
| **Příslušné jazyky** | C# 8.0 + |
| **Hodnoty** | `true`– Raději použijte `switch` výraz (představený v jazyce C# 8,0).<br /><br />`false`– Preferovat použití [příkazu switch](/dotnet/csharp/language-reference/keywords/switch) |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** |  Visual Studio 2019 verze 16.2  |

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

## <a name="see-also"></a>Viz také:

- [Konvence formátování](editorconfig-formatting-conventions.md)
- [Zásady vytváření názvů](editorconfig-naming-conventions.md)
- [Nastavení konvence kódování .NET pro EditorConfig](editorconfig-code-style-settings-reference.md)
