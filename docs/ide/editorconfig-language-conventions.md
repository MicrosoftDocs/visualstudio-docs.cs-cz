---
title: Jazykové konvence rozhraní .NET pro EditorConfig
ms.date: 09/23/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 471932f6a097879da194dc6bb4f18807f2323397
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542656"
---
# <a name="language-conventions"></a>Konvence jazyka

Jazykové konvence pro EditorConfig v aplikaci Visual Studio spadají do dvou kategorií: ty, které se C#vztahují na Visual Basic a a C# ty, které jsou specifické. Jazykové konvence mají vliv na to, jak se používají různé aspekty programovacího jazyka, například modifikátory a závorky.

> [!TIP]
> - Chcete-li zobrazit příklady kódu v upřednostňovaném programovacím jazyce, vyberte jej pomocí nástroje pro výběr jazyka v pravém horním rohu okna prohlížeče.
>
>   ![Ovládací prvek pro výběr jazyka kódu](media/code-language-picker.png)
>
> - Pomocí odkazu **v tomto článku** můžete přejít na jiné části stránky.

## <a name="rule-format"></a>Formát pravidla

Pravidla pro jazykové konvence mají následující obecný formát:

`option_name = value:severity`

Pro každou jazykovou konvenci zadáte hodnotu, která definuje, kdy nebo kdy chcete styl preferovat. Mnoho pravidel přijímá hodnotu `true` (preferovat tento styl) nebo `false` (nepreferovat tento styl). Jiná pravidla přijímají hodnoty, například `when_on_single_line` nebo `never`. Druhá část pravidla určuje [závažnost](#severity-levels).

::: moniker range=">=vs-2019"

> [!NOTE]
> Vzhledem k tomu, že jsou jazykové konvence vynutily analyzátory, můžete také nastavit jejich závažnost pomocí výchozí syntaxe konfigurace pro analyzátory. Syntaxe má formu `dotnet_diagnostic.<rule ID>.severity = <severity>`, například `dotnet_diagnostic.IDE0040.severity = silent`. Další informace najdete v tématu [nastavení závažnosti pravidla v souboru EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file).

::: moniker-end

## <a name="severity-levels"></a>Úrovně závažnosti

Závažnost jazykové konvence určuje úroveň, na které se má tento styl vyhovět. V následující tabulce jsou uvedeny možné hodnoty závažnosti a jejich důsledky:

Závažnost | Efekt
:------- | ------
`error` | Při porušení tohoto pravidla stylu zobrazit chybu kompilátoru.
`warning` | Při porušení tohoto pravidla stylu zobrazit upozornění kompilátoru.
`suggestion` | Když je toto pravidlo stylu porušeno, zobrazte ho uživateli jako návrh. Návrhy se zobrazí jako tři šedé tečky pod prvními dvěma znaky.
`silent` | Nezobrazovat uživateli žádné údaje, pokud je toto pravidlo porušeno. Funkce pro generování kódu generují kód v tomto stylu, ale. Pravidla s `silent` závažností se účastní vyčištění a zobrazují se v nabídce **rychlé akce a refaktoringy** .
`none` | Nezobrazovat uživateli žádné údaje, pokud je toto pravidlo porušeno. Funkce pro generování kódu generují kód v tomto stylu, ale. Pravidla s `none` závažností se nikdy neobjevují v nabídce **rychlé akce a refaktoringy** . Ve většině případů se to považuje za "zakázané" nebo "ignorované".

::: moniker range=">=vs-2019"

## <a name="automatically-configure-code-styles"></a>Automaticky konfigurovat styly kódu

Počínaje verzí Visual Studio 2019 verze 16,3 můžete nakonfigurovat pravidla stylu kódu z nabídky návrhy [rychlých akcí](quick-actions.md) poté, co dojde k porušení stylu.

Změna konvence stylu kódu:

1. Najeďte myší na vlnovkou v editoru a pak otevřete nabídku žárovky, která se zobrazí. Vyberte možnost **Konfigurovat nebo potlačit problémy** , > **konfigurovat ID pravidla \<> stylu kódu**.

   ![Konfigurace stylu kódu z nabídky světlé žárovky v aplikaci Visual Studio](media/vs-2019/configure-code-style.png)

2. Odtud vyberte jednu z možností stylu kódu.

   ![Konfigurovat nastavení stylu kódu](media/vs-2019/configure-code-style-setting.png)

   Visual Studio přidá nebo upraví konfigurační nastavení v souboru EditorConfig, jak je znázorněno v poli Náhled.

Chcete-li změnit závažnost porušení stylu kódu, postupujte podle stejných kroků, ale vyberte možnost **nakonfigurovat \<ID pravidla > závažnost** místo **konfigurace id pravidla \<> stylu kódu**. Další informace najdete v tématu [automatické konfigurace závažnosti pravidla](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity).

::: moniker-end

## <a name="net-code-style-settings"></a>Nastavení stylu kódu .NET

Pravidla stylu v této části platí pro C# i Visual Basic.

- [Kvalifikátory "This." a "já"](#this-and-me)
  - dotnet\_Style\_kvalifikaci\_for_field
  - dotnet\_style\_qualification\_for_property
  - dotnet\_Style\_kvalifikaci\_for_method
  - dotnet\_Style\_kvalifikaci\_for_event
- [Klíčová slova jazyka namísto názvů typů rozhraní pro odkazy na typy](#language-keywords)
  - dotnet\_Style\_předdefinovaný typ\_\_pro\_místní\_parameters_members
  - dotnet\_style\_predefined\_type\_for\_member_access
- [Předvolby modifikátoru](#normalize-modifiers)
  - dotnet\_Style\_vyžadovat\_accessibility_modifiers
  - csharp\_preferred\_modifier_order
  - visual\_basic\_preferred\_modifier_order
  - dotnet\_Style\_pole ReadOnly\_
- [Předvolby závorek](#parentheses-preferences)
  - dotnet\_Style\_závorky\_v\_aritmetických\_binárních\_ch operátorů
  - dotnet\_Style\_závorky\_v\_dalších\_binárních\_ch operátorů
  - dotnet\_Style\_závorky\_v\_dalších\_ch operátorů
  - dotnet\_Style\_závorky\_v\_relační\_binární\_operátory
- [Předvolby na úrovni výrazu](#expression-level-preferences)
  - dotnet\_style\_object_initializer
  - \_\_stylu dotnet collection_initializer
  - dotnet\_Style\_Explicit\_tuple_names
  - dotnet\_Style\_preferovat\_odvoditelné\_tuple_names
  - dotnet\_Style\_preferovat\_odvozený\_anonymní\_typ\_member_names
  - dotnet\_style\_prefer\_auto\_properties
  - dotnet\_Style\_preferovat\_je\_null\_\_metoda\_rovnosti\_
  - dotnet\_Style\_preferovat\_podmíněný\_výraz\_over\_přiřazení
  - dotnet\_Style\_preferovat\_podmíněný\_výraz\_nad\_návrat
  - dotnet\_Style\_preferovat\_složené\_přiřazení
- [Předvolby kontroly "null"](#null-checking-preferences)
  - dotnet\_style\_coalesce_expression
  - dotnet\_style\_null_propagation

### <a name="this-and-me"></a>"This." a "já". kvalifikátory

Toto pravidlo stylu lze použít pro pole, vlastnosti, metody nebo události. Hodnota **true** znamená, že symbol kódu má být před `this.` v C# nebo `Me.` v Visual Basic. Hodnota **false** znamená, že by element Code _neměl_ být v `this.` nebo `Me.`.

Tato pravidla by se mohla objevit v souboru *. editorconfig* následujícím způsobem:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>dotnet\_Style\_kvalifikaci\_for_field

|||
|-|-|
| **Název pravidla** | dotnet_style_qualification_for_field |
| **ID pravidla** | IDE0003 a IDE0009 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – preferovat pole, která se mají předcházet `this.` v C# nebo `Me.` v Visual Basic<br /><br />`false` – preferovat pole, která _nemají_ být uvozená `this.` nebo `Me.` |
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

#### <a name="dotnet_style_qualification_for_property"></a>dotnet\_style\_qualification\_for_property

|||
|-|-|
| **Název pravidla** | dotnet_style_qualification_for_property |
| **ID pravidla** | IDE0003 a IDE0009 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – upřednostnit vlastnosti, které se mají předcházet `this.` v C# nebo `Me.` v Visual Basic<br /><br />`false` – upřednostnit vlastnosti, které _nemají_ být uvozeny `this.` nebo `Me.` |
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

#### <a name="dotnet_style_qualification_for_method"></a>dotnet\_Style\_kvalifikaci\_for_method

|||
|-|-|
| **Název pravidla** | dotnet_style_qualification_for_method |
| **ID pravidla** | IDE0003 a IDE0009 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – preferovat metody s `this.` v C# nebo `Me.` v Visual Basic.<br /><br />`false` – preferovat metody, které _nemají_ být uvozeny `this.` nebo `Me.`. |
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

#### <a name="dotnet_style_qualification_for_event"></a>dotnet\_Style\_kvalifikaci\_for_event

|||
|-|-|
| **Název pravidla** | dotnet_style_qualification_for_event |
| **ID pravidla** | IDE0003 a IDE0009 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – preferovat události, které se mají předcházet `this.` v C# nebo `Me.` v Visual Basic.<br /><br />`false` – preferovat události, které _nemají_ být uvozeny `this.` nebo `Me.`. |
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

### <a name="language-keywords"></a>Klíčová slova jazyka namísto názvů typů rozhraní pro odkazy na typy

Toto pravidlo stylu lze použít pro lokální proměnné, parametry metody a členy třídy nebo jako samostatné pravidlo pro typ výrazů přístupu členů. Hodnota **true** znamená preferovat klíčové slovo jazyka (například `int` nebo `Integer`) namísto názvu typu (například `Int32`) pro typy, které mají klíčové slovo reprezentovatelné. Hodnota **false** znamená raději název typu místo klíčového slova Language.

Tato pravidla by se mohla objevit v souboru *. editorconfig* následujícím způsobem:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>dotnet\_Style\_předdefinovaný typ\_\_pro\_místní\_parameters_members

|||
|-|-|
| **Název pravidla** | dotnet_style_predefined_type_for_locals_parameters_members |
| **ID pravidla** | IDE0012 a IDE0014 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – preferovat klíčové slovo jazyka pro lokální proměnné, parametry metody a členy třídy namísto názvu typu pro typy, které mají klíčové slovo k reprezentaci<br /><br />`false` – upřednostňuje název typu pro lokální proměnné, parametry metody a členy třídy místo klíčového slova Language. |
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

#### <a name="dotnet_style_predefined_type_for_member_access"></a>dotnet\_style\_predefined\_type\_for\_member_access

|||
|-|-|
| **Název pravidla** | dotnet_style_predefined_type_for_member_access |
| **ID pravidla** | IDE0013 a IDE0015 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – preferovat klíčové slovo jazyka pro výrazy přístupu členů namísto názvu typu, pro typy, které mají klíčové slovo, které je reprezentovat<br /><br />`false` – raději název typu pro výrazy přístupu členů místo klíčového slova Language |
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

### <a name="normalize-modifiers"></a>Předvolby modifikátoru

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

#### <a name="dotnet_style_require_accessibility_modifiers"></a>dotnet\_Style\_vyžadovat\_accessibility_modifiers

|||
|-|-|
| **Název pravidla** | dotnet_style_require_accessibility_modifiers |
| **ID pravidla** | IDE0040 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always` – doporučuje se zadat Modifikátory dostupnosti.<br /><br />`for_non_interface_members` – upřednostnit Modifikátory dostupnosti, které mají být deklarovány s výjimkou členů veřejných rozhraní. (To je stejné jako **Always** a bylo přidáno pro budoucí kontrolu, pokud C# nástroj přidá výchozí metody rozhraní.)<br /><br />`never` – nedoporučujeme zadat Modifikátory dostupnosti.<br /><br />`omit_if_default` – preferovat Modifikátory dostupnosti, které mají být zadány, s výjimkou případů, kdy jsou výchozím modifikátorem. |
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

|||
|-|-|
| **Název pravidla** | csharp_preferred_modifier_order |
| **ID pravidla** | IDE0036 |
| **Příslušné jazyky** | C# |
| **Hodnoty** | Jeden nebo více C# modifikátorů, například `public`, `private`a `protected` |
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

|||
|-|-|
| **Název pravidla** | visual_basic_preferred_modifier_order |
| **ID pravidla** | IDE0036 |
| **Příslušné jazyky** | Visual Basic |
| **Hodnoty** | Jeden nebo více modifikátorů Visual Basic, například `Partial`, `Private`a `Public` |
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

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|||
|-|-|
| **Název pravidla** | dotnet_style_readonly_field |
| **ID pravidla** | IDE0044 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – preferovat, že pole by měla být označenaC#pomocí `readonly` () nebo `ReadOnly` (Visual Basic), pokud jsou pouze přiřazena vložená nebo uvnitř konstruktoru<br /><br />`false` – Neurčovat, zda mají být pole označena `readonly` (C#) nebo `ReadOnly` (Visual Basic) |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2017 verze 15,7 |

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

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>dotnet\_Style\_závorky\_v\_aritmetické\_binary_operators

|||
|-|-|
| **Název pravidla** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **ID pravidla** | IDE0047 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always_for_clarity` – preferovat kulaté závorky pro objasnění aritmetického operátoru (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) priority<br /><br />`never_if_unnecessary` – nedoporučuje se používat kulaté závorky, pokud aritmetický operátor (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) má zjevné přednost. |
| **Výchozí nastavení sady Visual Studio** | `always_for_clarity:silent` |
| **Představená verze** | Visual Studio 2017 verze 15.8 |

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

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>dotnet\_Style\_závorkách\_v\_relačních\_binary_operators

|||
|-|-|
| **Název pravidla** | dotnet_style_parentheses_in_relational_binary_operators |
| **ID pravidla** | IDE0047 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always_for_clarity` – upřednostnit kulaté závorky k objasnění relačních operátorů (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) priority<br /><br />`never_if_unnecessary` – nedoporučuje se používat závorky, když relační operátor (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) má zřejmou přednost. |
| **Výchozí nastavení sady Visual Studio** | `always_for_clarity:silent` |
| **Představená verze** | Visual Studio 2017 verze 15.8 |

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

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>dotnet\_Style\_závorkách\_v\_dalších\_binary_operators

|||
|-|-|
| **Název pravidla** | dotnet_style_parentheses_in_other_binary_operators |
| **ID pravidla** | IDE0047 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always_for_clarity` – upřednostnit kulaté závorky k vysvětlení jiné priority binárního operátoru (`&&`, `||`, `??`)<br /><br />`never_if_unnecessary` – nedoporučuje se používat závorky, když je jiný binární operátor (`&&`, `||`, `??`) zjevný. |
| **Výchozí nastavení sady Visual Studio** | `always_for_clarity:silent` |
| **Představená verze** | Visual Studio 2017 verze 15.8 |

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

#### <a name="dotnet_style_parentheses_in_other_operators"></a>dotnet\_Style\_závorkách\_v\_other_operators

|||
|-|-|
| **Název pravidla** | dotnet_style_parentheses_in_other_operators |
| **ID pravidla** | IDE0047 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `always_for_clarity` – preferovat závorky k objasnění priority operátoru<br /><br />`never_if_unnecessary` – nedoporučuje se používat závorky, když je priorita operátoru zřejmá. |
| **Výchozí nastavení sady Visual Studio** | `never_if_unnecessary:silent` |
| **Představená verze** | Visual Studio 2017 verze 15.8 |

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

#### <a name="dotnet_style_object_initializer"></a>dotnet\_style\_object_initializer

|||
|-|-|
| **Název pravidla** | dotnet_style_object_initializer |
| **ID pravidla** | IDE0017 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – preferovat objekty, které se mají inicializovat pomocí inicializátorů objektů, pokud je to možné<br /><br />`false` – preferovat objekty, které se *nemají* inicializovat pomocí inicializátorů objektů |
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

#### <a name="dotnet_style_collection_initializer"></a>\_\_stylu dotnet collection_initializer

|||
|-|-|
| **Název pravidla** | dotnet_style_collection_initializer |
| **ID pravidla** | IDE0028 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – preferovat kolekce, které se mají inicializovat pomocí inicializátorů kolekce, pokud je to možné<br /><br />`false` – preferovat kolekce, které se *nemají* inicializovat pomocí inicializátorů kolekcí. |
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

#### <a name="dotnet_style_explicit_tuple_names"></a>dotnet\_Style\_Explicit\_tuple_names

|||
|-|-|
| **Název pravidla** | dotnet_style_explicit_tuple_names |
| **ID pravidla** | IDE0033 |
| **Příslušné jazyky** | C#7.0 + a Visual Basic 15 + |
| **Hodnoty** | `true` – preferovat názvy řazené kolekce členů podle vlastností ItemX<br /><br />`false` – preferovat vlastnosti ItemX názvů řazených kolekcí členů |
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

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>dotnet\_Style\_preferovat\_odvoditelné\_tuple_names

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_inferred_tuple_names |
| **ID pravidla** | IDE0037 |
| **Příslušné jazyky** | C#7.1 + a Visual Basic 15 + |
| **Hodnoty** | `true` – preferovat odvozené názvy elementů řazené kolekce členů<br /><br />`false` – preferovat explicitní názvy elementů řazené kolekce členů |
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

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>dotnet\_Style\_preferovat\_odvozený\_anonymní\_typ\_member_names

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **ID pravidla** | IDE0037 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – preferovat odvozené názvy členů anonymního typu<br /><br />`false` – preferovat explicitní názvy členů anonymního typu |
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

#### <a name="dotnet_style_prefer_auto_properties"></a>dotnet\_style\_prefer\_auto\_properties

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_auto_properties |
| **ID pravidla** | IDE0032 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – preferovat autoproperties přes vlastnosti pomocí soukromých zálohovaných polí<br /><br />`false` – preferovat vlastnosti soukromými zálohovanými poli přes autoproperties |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2017 verze 15,7 |

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

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_Style\_preferovat\_je\_null\_\_metoda\_rovnosti\_

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **ID pravidla** | IDE0041 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – raději použít kontrolu null s porovnáváním vzorů přes `object.ReferenceEquals`<br /><br />`false` – preferovat `object.ReferenceEquals` při kontrole s hodnotou null se porovnáváním vzorů |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2017 verze 15,7 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>dotnet\_style\_prefer\_conditional\_expression\_over_assignment

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_conditional_expression_over_assignment |
| **ID pravidla** | IDE0045 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – upřednostnit přiřazení s ternárním podmíněným příkazem if-else<br /><br />`false` – preferovat přiřazení pomocí příkazu if-else přes Ternární podmíněný |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2017 verze 15.8 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>dotnet\_Style\_preferovat\_podmíněný\_Expression\_over_return

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_conditional_expression_over_return |
| **ID pravidla** | IDE0046 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – preferovat návratové příkazy pro použití ternárního podmíněného příkazu if-else<br /><br />`false` – preferovat návratové příkazy pro použití příkazu if-else nad Ternární podmínkou |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2017 verze 15.8 |

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

#### <a name="dotnet_style_prefer_compound_assignment"></a>dotnet\_Style\_preferovat\_složené\_přiřazení

|||
|-|-|
| **Název pravidla** | dotnet_style_prefer_compound_assignment |
| **ID pravidla** | IDE0054 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – preferovat výrazy [složeného přiřazení](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment)<br /><br />`false` – nepreferovat výrazy složeného přiřazení |
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
```

#### <a name="dotnet_style_coalesce_expression"></a>dotnet\_style\_coalesce_expression

|||
|-|-|
| **Název pravidla** | dotnet_style_coalesce_expression |
| **ID pravidla** | IDE0029 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | `true` – upřednostnit hodnoty null slučovacích výrazů pro kontrolu ternárních operátorů<br /><br />`false` – upřednostnit Ternární operátor zaškrtnutí na hodnoty null slučovacích výrazů |
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

#### <a name="dotnet_style_null_propagation"></a>dotnet\_style\_null_propagation

|||
|-|-|
| **Název pravidla** | dotnet_style_null_propagation |
| **ID pravidla** | IDE0031 |
| **Příslušné jazyky** | C#6.0 + a Visual Basic 14 + |
| **Hodnoty** | `true` – preferovat použití podmíněného operátoru null, pokud je to možné<br /><br />`false` – raději použít kontrolu Ternární hodnoty null, pokud je to možné |
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

## <a name="net-code-quality-settings"></a>Nastavení kvality kódu .NET

Pravidla kvality v této části se vztahují na kód C# i Visual Basic. Slouží ke konfiguraci analyzátorů kódu, které jsou integrovány do integrovaného vývojového prostředí (IDE) sady Visual Studio. Informace o konfiguraci analyzátorů FxCop pomocí souboru EditorConfig najdete v tématu [Konfigurace analyzátorů FxCop](../code-quality/configure-fxcop-analyzers.md).

- [Předvolby parametrů](#parameter-preferences)
  - dotnet\_\_kvality kódu\_nepoužitými parametry\_

### <a name="parameter-preferences"></a>Předvolby parametrů

Pravidla kvality v této části se týkají parametrů metod.

Tato pravidla by se mohla objevit v souboru *. editorconfig* následujícím způsobem:

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>dotnet\_\_kvality kódu\_nepoužitými parametry\_

|||
|-|-|
| **Název pravidla** | dotnet_code_quality_unused_parameters |
| **ID pravidla** | IDE0060 |
| **Příslušné jazyky** | C# a Visual Basic |
| **Hodnoty** | metody `all`-Flag s jakýmkoli přístupným příznakem, který obsahuje nepoužívané parametry<br /><br />`non_public` – příznak pouze neveřejné metody, které obsahují nepoužité parametry |
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

## <a name="c-code-style-settings"></a>C#nastavení stylu kódu

Pravidla stylu v této části platí pouze pro C# .

- [Implicitní a explicitní typy](#implicit-and-explicit-types)
  - CSharp\_Style\_var\_pro\_sestavené\_in_types
  - csharp\_style\_var\_when\_type\_is_apparent
  - csharp\_style\_var_elsewhere
- [Členové tvoření výrazy](#expression-bodied-members)
  - výraz\_\_CSharp stylu\_bodied_methods
  - csharp\_style\_expression\_bodied_constructors
  - csharp\_style\_expression\_bodied_operators
  - csharp\_style\_expression\_bodied_properties
  - csharp\_style\_expression\_bodied_indexers
  - csharp\_style\_expression\_bodied_accessors
  - výraz\_\_CSharp stylu\_bodied_lambdas
  - CSharp\_Style\_Expression\_těle\_local_functions
- [Porovnávání vzorů](#pattern-matching)
  - CSharp\_stylu\_\_porovnávání\_po\_\_\_cast_check
  - CSharp\_stylu\_\_porovnávání\_po\_s\_\_
- [Vložené deklarace proměnných](#inlined-variable-declarations)
  - CSharp\_styl\_vložené\_variable_declaration
- [Předvolby na úrovni výrazu](#c-expression-level-preferences)
  - csharp\_prefer\_simple\_default_expression
- [Předvolby kontroly "null"](#c-null-checking-preferences)
  - csharp\_style\_throw_expression
  - csharp\_style\_conditional\_delegate_call
- [Předvolby bloku kódu](#code-block-preferences)
  - csharp\_prefer_braces
- [Předvolby nepoužité hodnoty](#unused-value-preferences)
  - CSharp\_Style\_nepoužitou\_ovou hodnotou\_výrazu\_statement_preference
  - CSharp\_Style\_nepoužitou\_ovou hodnotou\_assignment_preference
- [Předvolby indexu a rozsahu](#index-and-range-preferences)
  - CSharp\_styl\_preferovat\_index_operator
  - CSharp\_styl\_preferovat\_range_operator
- [Různé předvolby](#miscellaneous-preferences)
  - CSharp\_styl\_Dekonstruovaný\_variable_declaration
  - CSharp\_Style\_vzor\_místní\_nad\_anonymous_function
  - CSharp\_používající direktivu\_\_umístění
  - CSharp\_preferovat\_statické\_local_function
  - CSharp\_preferovat\_jednoduché\_using_statement
  - CSharp\_styl\_preferovat\_switch_expression

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

#### <a name="csharp_style_var_for_built_in_types"></a>CSharp\_Style\_var\_pro\_sestavené\_in_types

|||
|-|-|
| **Název pravidla** | csharp_style_var_for_built_in_types |
| **ID pravidla** | IDE0007 a IDE0008 |
| **Příslušné jazyky** | C#  |
| **Hodnoty** | `true` – preferovat `var` se používá k deklaraci proměnných s integrovanými systémovými typy, jako je například `int`<br /><br />`false` – preferovat explicitní typ přes `var` k deklaraci proměnných s integrovanými systémovými typy, jako je například `int` |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>csharp\_style\_var\_when\_type\_is_apparent

|||
|-|-|
| **Název pravidla** | csharp_style_var_when_type_is_apparent |
| **ID pravidla** | IDE0007 a IDE0008 |
| **Příslušné jazyky** | C#  |
| **Hodnoty** | `true` – preferovat `var`, pokud je již tento typ uveden na pravé straně výrazu deklarace<br /><br />`false` – preferovat explicitní typ přes `var`, pokud je tento typ již uveden na pravé straně výrazu deklarace |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>csharp\_style\_var_elsewhere

|||
|-|-|
| **Název pravidla** | csharp_style_var_elsewhere |
| **ID pravidla** | IDE0007 a IDE0008 |
| **Příslušné jazyky** | C#  |
| **Hodnoty** | `true` – preferovat `var` přes explicitní typ ve všech případech, pokud není přepsán jiným pravidlem stylu kódu<br /><br />`false` – preferovat explicitní typ přes `var` ve všech případech, pokud není přepsán jiným pravidlem stylu kódu. |
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

#### <a name="csharp_style_expression_bodied_methods"></a>výraz\_\_CSharp stylu\_bodied_methods

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_methods |
| **ID pravidla** | IDE0022 |
| **Příslušné jazyky** | C#6.0 +  |
| **Hodnoty** | `true` – preferovat texty výrazu pro metody<br /><br />`when_on_single_line` – preferovat tělo výrazu pro metody, když budou být jedním řádkem<br /><br />`false` – preferovat blokové texty pro metody |
| **Výchozí nastavení sady Visual Studio** | `false:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>csharp\_style\_expression\_bodied_constructors

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_constructors |
| **ID pravidla** | IDE0021 |
| **Příslušné jazyky** | C#7.0 + |
| **Hodnoty** | `true` – preferovat tělo výrazu pro konstruktory<br /><br />`when_on_single_line` – preferovat tělo výrazu pro konstruktory, když budou být jedním řádkem<br /><br />`false` – preferovat blokové texty pro konstruktory |
| **Výchozí nastavení sady Visual Studio** | `false:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>csharp\_style\_expression\_bodied_operators

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_operators |
| **ID pravidla** | IDE0023 a IDE0024 |
| **Příslušné jazyky** | C#7.0 + |
| **Hodnoty** | `true` – preferovat tělo výrazu pro operátory<br /><br />`when_on_single_line` – preferovat tělo výrazu pro operátory, pokud budou být jedním řádkem<br /><br />`false` – preferovat blokové texty pro operátory |
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

#### <a name="csharp_style_expression_bodied_properties"></a>csharp\_style\_expression\_bodied_properties

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_properties |
| **ID pravidla** | IDE0025 |
| **Příslušné jazyky** | C#7.0 + |
| **Hodnoty** | `true` – preferovat tělo výrazu pro vlastnosti<br /><br />`when_on_single_line` – preferovat tělo výrazu pro vlastnosti, když budou být jedním řádkem<br /><br />`false` – preferovat blokové texty pro vlastnosti |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>csharp\_style\_expression\_bodied_indexers

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_indexers |
| **ID pravidla** | IDE0026 |
| **Příslušné jazyky** | C#7.0 + |
| **Hodnoty** | `true` – preferovat tělo výrazu pro indexery<br /><br />`when_on_single_line` – preferovat tělo výrazu pro indexery, pokud budou představovat jeden řádek<br /><br />`false` – preferovat blokové texty pro indexery |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>csharp\_style\_expression\_bodied_accessors

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_accessors |
| **ID pravidla** | IDE0027 |
| **Příslušné jazyky** | C#7.0 + |
| **Hodnoty** | `true` – preferovat tělo výrazu pro přistupující objekty<br /><br />`when_on_single_line` – preferovat těla výrazů pro přistupující objekty, když budou být jedním řádkem<br /><br />`false` – preferovat zablokované texty pro přistupující objekty |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>výraz\_\_CSharp stylu\_bodied_lambdas

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_lambdas |
| **ID pravidla** | IDE0053 |
| **Hodnoty** | `true` – preferovat texty výrazů pro lambda<br /><br />`when_on_single_line` – preferovat výrazy výrazů pro lambda, pokud budou být jedním řádkem<br /><br />`false` – preferovat blokové texty pro výrazy lambda |
| **Výchozí nastavení sady Visual Studio** | `true:silent` |

Příklady kódu:

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>CSharp\_Style\_Expression\_těle\_local_functions

Počínaje C# 7,0 C# podporuje [místní funkce](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Lokální funkce jsou soukromé metody typu, které jsou vnořené v jiném členu.

|||
|-|-|
| **Název pravidla** | csharp_style_expression_bodied_local_functions |
| **ID pravidla** | IDE0061 |
| **Příslušné jazyky** | C#7.0 + |
| **Hodnoty** | `true` – preferovat texty výrazu pro místní funkce<br /><br />`when_on_single_line` – preferovat tělo výrazu pro místní funkce, když budou to jeden řádek<br /><br />`false` – preferovat blokové texty pro místní funkce |
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

Pravidla stylu v této části se týkají použití porovnávání se [vzorci](/dotnet/csharp/pattern-matching) v C#.

Příklad souboru *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>CSharp\_stylu\_\_porovnávání\_po\_\_\_cast_check

|||
|-|-|
| **Název pravidla** | csharp_style_pattern_matching_over_is_with_cast_check |
| **ID pravidla** | IDE0020 |
| **Příslušné jazyky** | C#7.0 + |
| **Hodnoty** | `true` – preferovat porovnávání vzorů místo `is` výrazů s přetypováními typů<br /><br />`false` – preferovat `is` výrazy s přetypováními typů namísto porovnávání vzorů |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>CSharp\_stylu\_\_porovnávání\_po\_s\_\_

|||
|-|-|
| **Název pravidla** | csharp_style_pattern_matching_over_as_with_null_check |
| **ID pravidla** | IDE0019 |
| **Příslušné jazyky** | C#7.0 + |
| **Hodnoty** | `true` – preferovat porovnávání vzorů místo `as` výrazů s kontrolami null k určení, jestli je něco konkrétního typu<br /><br />`false` – preferovat `as` výrazy s nulovými kontrolami namísto porovnávání vzorů k určení, jestli je něco konkrétního typu |
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

Toto pravidlo stylu se týká, zda jsou proměnné `out` deklarovány jako vložené nebo ne. Počínaje C# 7 můžete [deklarovat proměnnou out v seznamu argumentů volání metody](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), nikoli v deklaraci samostatné proměnné.

#### <a name="csharp_style_inlined_variable_declaration"></a>CSharp\_styl\_vložené\_variable_declaration

|||
|-|-|
| **Název pravidla** | csharp_style_inlined_variable_declaration |
| **ID pravidla** | IDE0018 |
| **Příslušné jazyky** | C#7.0 + |
| **Hodnoty** | `true` – preferovat `out` proměnných, které se mají deklarovat jako vložené v seznamu argumentů volání metody, pokud je to možné<br /><br />`false` – preferovat `out` proměnné, které se mají deklarovat před voláním metody |
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

### <a name="c-expression-level-preferences"></a>C#Předvolby na úrovni výrazu

Pravidla stylu v této části se týkají předvoleb na úrovni výrazu.

Příklad souboru *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>csharp\_prefer\_simple\_default_expression

Toto pravidlo stylu se týká použití [literálu`default` pro výrazy výchozích hodnot](/dotnet/csharp/language-reference/operators/default#default-literal) , když kompilátor může odvodit typ výrazu.

|||
|-|-|
| **Název pravidla** | csharp_prefer_simple_default_expression |
| **ID pravidla** | IDE0034 |
| **Příslušné jazyky** | C#7.1 +  |
| **Hodnoty** | `true` – preferovat `default` přes `default(T)`<br /><br />`false` – preferovat `default(T)` přes `default` |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>C#předvolby pro kontrolu hodnoty null

Tato pravidla stylu se týkají syntaxe kolem `null` kontroly, včetně použití výrazů `throw` nebo `throw` příkazů a zda má být provedena kontrola s hodnotou null nebo použití operátoru podmíněného sloučení (`?.`) při volání [výrazu lambda](/dotnet/csharp/lambda-expressions).

Příklad souboru *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>csharp\_style\_throw_expression

|||
|-|-|
| **Název pravidla** | csharp_style_throw_expression |
| **ID pravidla** | IDE0016 |
| **Příslušné jazyky** | C#7.0 + |
| **Hodnoty** | `true` – raději použít výrazy `throw` namísto příkazů `throw`<br /><br />`false` – raději použít příkazy `throw` namísto `throw` výrazů |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>csharp\_style\_conditional\_delegate_call

|||
|-|-|
| **Název pravidla** | csharp_style_conditional_delegate_call |
| **ID pravidla** | IDE0041 |
| **Příslušné jazyky** | C#6.0 +  |
| **Hodnoty** | `true` – při vyvolání výrazu lambda použijte při volání výrazu lambda (`?.`) použití operátoru podmíněného sloučení (), nemusíte provádět kontrolu s hodnotou null.<br /><br />`false` – před voláním výrazu lambda se doporučuje provést kontrolu null, místo použití operátoru podmíněného slučování (`?.`). |
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

#### <a name="csharp_prefer_braces"></a>CSharp\_preferovat\_závorky

|||
|-|-|
| **Název pravidla** | csharp_prefer_braces |
| **ID pravidla** | IDE0011 |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` – preferovat složené závorky i pro jeden řádek kódu<br /><br />`false` – nepreferovat žádné složené závorky, pokud je povoleno<br /><br />`when_multiline` – preferovat složené závorky na více řádcích |
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

|||
|-|-|
| **Název pravidla** | csharp_style_unused_value_expression_statement_preference |
| **ID pravidla** | IDE0058 |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `discard_variable` – preferovat přiřazení nepoužitého výrazu k [zahození](/dotnet/csharp/discards) <br /><br />`unused_local_variable` – raději přiřaďte nepoužitý výraz místní proměnné. |
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
| **Příslušné jazyky** | C# |
| **Hodnoty** | `discard_variable` – při přiřazování hodnoty, která se nepoužívá, je vhodné použít [zahození](/dotnet/csharp/discards)<br /><br />`unused_local_variable` – raději použít místní proměnnou při přiřazování hodnoty, která se nepoužívá |
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

Tato pravidla stylu se týkají použití operátorů index a rozsah, které jsou k dispozici v C# 8,0 a novějších verzích.

Příklad souboru *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>CSharp\_styl\_preferovat\_index_operator

|||
|-|-|
| **Název pravidla** | csharp_style_prefer_index_operator |
| **ID pravidla** | IDE0056 |
| **Příslušné jazyky** | C#8.0 + |
| **Hodnoty** | `true` – preferovat použití operátoru `^` při výpočtu indexu z konce kolekce<br /><br />`false` – nedoporučuje se používat operátor `^` při výpočtu indexu z konce kolekce. |
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

#### <a name="csharp_style_prefer_range_operator"></a>CSharp\_styl\_preferovat\_range_operator

|||
|-|-|
| **Název pravidla** | csharp_style_prefer_range_operator |
| **ID pravidla** | IDE0057 |
| **Příslušné jazyky** | C#8.0 + |
| **Hodnoty** | `true` – při extrakci "řezu" kolekce je vhodné použít operátor rozsahu `..`<br /><br />`false` – nedoporučuje se používat operátor rozsahu `..` při extrakci "řezu" kolekce. |
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

#### <a name="csharp_style_deconstructed_variable_declaration"></a>CSharp\_styl\_Dekonstruovaný\_variable_declaration

|||
|-|-|
| **Název pravidla** | csharp_style_deconstructed_variable_declaration |
| **ID pravidla** | IDE0042 |
| **Příslušné jazyky** | C#7.0 + |
| **Hodnoty** | `true` – preferovat deklaraci dekonstruovaných proměnných<br /><br />`false` – nepreferovat dekonstrukci v deklaracích proměnných |
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

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>CSharp\_Style\_vzor\_místní\_nad\_anonymous_function

Počínaje C# 7,0 C# podporuje [místní funkce](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Lokální funkce jsou soukromé metody typu, které jsou vnořené v jiném členu.

|||
|-|-|
| **Název pravidla** | csharp_style_pattern_local_over_anonymous_function |
| **ID pravidla** | IDE0039 |
| **Příslušné jazyky** | C#7.0 + |
| **Hodnoty** | `true` – upřednostnit místní funkce přes anonymní funkce<br /><br />`false` – upřednostnit anonymní funkce nad místními funkcemi |
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

#### <a name="csharp_using_directive_placement"></a>CSharp\_používající\_directive_placement

|||
|-|-|
| **Název pravidla** | csharp_using_directive_placement |
| **ID pravidla** | IDE0065 |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `outside_namespace` – preferovat direktivy `using`, které se mají umístit mimo obor názvů<br /><br />`inside_namespace` – preferovat `using` direktivy, které mají být umístěny uvnitř oboru názvů |
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

#### <a name="csharp_prefer_static_local_function"></a>CSharp\_preferovat\_statické\_local_function

|||
|-|-|
| **Název pravidla** | csharp_prefer_static_local_function |
| **ID pravidla** | IDE0062 |
| **Příslušné jazyky** | C#8.0 + |
| **Hodnoty** | `true` – upřednostnit místní funkce, které mají být označeny `static`<br /><br />`false` – nedoporučujeme označení místních funkcí jako `static` |
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

#### <a name="csharp_prefer_simple_using_statement"></a>CSharp\_preferovat\_jednoduché\_using_statement

|||
|-|-|
| **Název pravidla** | csharp_prefer_simple_using_statement |
| **ID pravidla** | IDE0063 |
| **Příslušné jazyky** | C#8.0 + |
| **Hodnoty** | `true` – preferovat použití *jednoduchého* příkazu `using`<br /><br />`false` – nedoporučujeme používat *jednoduchý* příkaz `using` |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |

Příklady kódu:

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>CSharp\_styl\_preferovat\_switch_expression

|||
|-|-|
| **Název pravidla** | csharp_style_prefer_switch_expression |
| **ID pravidla** | IDE0066 |
| **Příslušné jazyky** | C#8.0 + |
| **Hodnoty** | `true` – raději použít výraz `switch` (představený s C# 8,0)<br /><br />`false` – preferovat použití [příkazu switch](/dotnet/csharp/language-reference/keywords/switch) |
| **Výchozí nastavení sady Visual Studio** | `true:suggestion` |
| **Představená verze** | Visual Studio 2019 verze 16,2 |

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
- [EditorConfig nastavení konvence psaní kódu .NET](editorconfig-code-style-settings-reference.md)
