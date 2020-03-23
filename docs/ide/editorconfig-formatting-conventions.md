---
title: Konvence formátování rozhraní .NET pro editorconfig
ms.date: 07/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 64f6a45b3a5cc49cd541ceb905356093ea4ec221
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589224"
---
# <a name="formatting-conventions"></a>Konvence formátování

Konvence formátování pro EditorConfig pro Visual Studio spadají do těchto kategorií:

- [Nastavení formátování rozhraní .NET](#net-formatting-settings)

- [Nastavení formátování Jazyka C#](#c-formatting-settings)

## <a name="rule-format"></a>Formát pravidla

Pravidla pro formátování konvencí mají následující formát:

`rule_name = value`

Pro mnoho pravidel zadáte `true` buď (upřednostňujte tento styl) `false` `value`nebo (nedávají tento styl) pro . Pro ostatní pravidla zadáte hodnotu, například `flush_left` nebo `before_and_after` popíšete, kdy a kde se má pravidlo použít. Nezadáte závažnost.

## <a name="net-formatting-settings"></a>Nastavení formátování rozhraní .NET

Pravidla formátování v této části platí pro kód jazyka C# a jazyka Visual Basic.

- [Uspořádání použití](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Uspořádání pomocí direktiv

Tato pravidla formátování se týkají řazení `using` a zobrazení `Imports` směrnic a příkazů.

Příklad souboru *.editorconfig:*

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a>directives_first řazení\_\_\_dotnet

|||
|-|-|
| **Název pravidla** | dotnet_sort_system_directives_first |
| **Použitelné jazyky** | C# a Visual Basic |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- Třídit `using` systém.* direktivy abecedně, a umístěte je před jinými pomocí směrnic.<br /><br />`false`- Neumisťuj `using` směrnice `using` systému před jiné směrnice. |
| **Výchozí nastavení sady Visual Studio** | `true` |

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

#### <a name="dotnet_separate_import_directive_groups"></a>dotnet\_\_samostatné\_\_dovozní direktivní skupiny

|||
|-|-|
| **Název pravidla** | dotnet_separate_import_directive_groups |
| **Použitelné jazyky** | C# a Visual Basic |
| **Zavedená verze** | Visual Studio 2017 verze 15.5 |
| **Hodnoty** | `true`- Umístěte prázdnou `using` čáru mezi skupiny direktiv.<br /><br />`false`- Neumisťuj prázdnou čáru mezi `using` skupiny direktiv. |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-settings"></a>Nastavení formátování Jazyka C#

Pravidla formátování v této části platí pouze pro kód jazyka C#.

- [Možnosti nového řádku](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Volby odsazení](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
  - csharp_indent_block_contents
  - csharp_indent_braces
  - csharp_indent_case_contents_when_block
- [Volby mezer](#spacing-options)
  - csharp_space_after_cast
  - csharp_space_after_keywords_in_control_flow_statements
  - csharp_space_between_parentheses
  - csharp_space_before_colon_in_inheritance_clause
  - csharp_space_after_colon_in_inheritance_clause
  - csharp_space_around_binary_operators
  - csharp_space_between_method_declaration_parameter_list_parentheses
  - csharp_space_between_method_declaration_empty_parameter_list_parentheses
  - csharp_space_between_method_declaration_name_and_open_parenthesis
  - csharp_space_between_method_call_parameter_list_parentheses
  - csharp_space_between_method_call_empty_parameter_list_parentheses
  - csharp_space_between_method_call_name_and_opening_parenthesis
  - csharp_space_after_comma
  - csharp_space_before_comma
  - csharp_space_after_dot
  - csharp_space_before_dot
  - csharp_space_after_semicolon_in_for_statement
  - csharp_space_before_semicolon_in_for_statement
  - csharp_space_around_declaration_statements
  - csharp_space_before_open_square_brackets
  - csharp_space_between_empty_square_brackets
  - csharp_space_between_square_brackets
- [Možnosti obtékání](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks

### <a name="new-line-options"></a>Možnosti nového řádku

Tato pravidla formátování se týkají použití nových řádků pro formátování kódu.

Příklad souboru *.editorconfig:*

```ini
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

#### <a name="csharp_new_line_before_open_brace"></a>csharp\_\_nový\_\_řádek před open_brace

Toto pravidlo se `{` týká, zda má být otevřená závorka umístěna na stejném řádku jako předchozí kód nebo na nový řádek. Pro toto pravidlo určíte **všechny**, **žádné**nebo jeden nebo více prvků kódu, jako jsou **metody** nebo **vlastnosti**, aby bylo možné definovat, kdy má být toto pravidlo použito. Chcete-li zadat více prvků kódu, oddělte je čárkou (,).

|||
|-|-|
| **Název pravidla** | csharp_new_line_before_open_brace |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `all`- Vyžadovat závorky, které mají být na novém řádku pro všechny výrazy ("Allman" styl).<br /><br />`none`- Vyžadovat, aby závorky byly na stejném řádku pro všechny výrazy ("K&R").<br /><br />`accessors`, `anonymous_methods` `anonymous_types`, `control_blocks` `events`, `indexers` `lambdas`, `local_functions` `methods`, `object_collection_array_initializers` `properties`, `types` , , , , - Vyžadovat, aby závorky byly na novém řádku pro zadaný kódový prvek (styl Allman). |
| **Výchozí nastavení sady Visual Studio** | `all` |

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

#### <a name="csharp_new_line_before_else"></a>csharp\_\_nový\_řádek before_else

|||
|-|-|
| **Název pravidla** | csharp_new_line_before_else |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- `else` Umístěte příkazy na nový řádek.<br /><br />`false`- `else` Umístěte příkazy na stejný řádek. |
| **Výchozí nastavení sady Visual Studio** | `true` |

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

#### <a name="csharp_new_line_before_catch"></a>csharp\_\_nový\_řádek before_catch

|||
|-|-|
| **Název pravidla** | csharp_new_line_before_catch |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- `catch` Umístěte příkazy na nový řádek.<br /><br />`false`- `catch` Umístěte příkazy na stejný řádek. |
| **Výchozí nastavení sady Visual Studio** | `true` |

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

#### <a name="csharp_new_line_before_finally"></a>csharp\_\_nový\_řádek before_finally

|||
|-|-|
| **Název pravidla** | csharp_new_line_before_finally |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- `finally` Vyžadovat, aby příkazy byly na novém řádku po závěrečné závorce.<br /><br />`false`- `finally` Vyžadovat, aby příkazy byly na stejném řádku jako uzavírací závorka. |
| **Výchozí nastavení sady Visual Studio** | `true` |

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

#### <a name="csharp_new_line_before_members_in_object_initializers"></a>csharp\_\_nový\_\_řádek\_\_před členy v object_initializers

|||
|-|-|
| **Název pravidla** | csharp_new_line_before_members_in_object_initializers |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- Vyžadovat členy inicializačních objektů, které mají být na samostatných řádcích<br /><br />`false`- Vyžadovat členy inicializačních objektů, které mají být na stejném řádku |
| **Výchozí nastavení sady Visual Studio** | `true` |

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

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a>csharp\_\_nový\_\_řádek\_\_před členy v anonymous_types

|||
|-|-|
| **Název pravidla** | csharp_new_line_before_members_in_anonymous_types |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- Vyžadovat, aby členové anonymních typů byli na samostatných řádcích<br /><br />`false`- Vyžadovat, aby členové anonymních typů byli na stejném řádku |
| **Výchozí nastavení sady Visual Studio** | `true` |

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

#### <a name="csharp_new_line_between_query_expression_clauses"></a>csharp_new_line_between_query_expression_clauses

|||
|-|-|
| **Název pravidla** | csharp_new_line_between_query_expression_clauses |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- Vyžadovat prvky klauzulí výrazu dotazu, které mají být na samostatných řádcích<br /><br />`false`- Vyžadovat prvky klauzule výrazdotaz být na stejném řádku |
| **Výchozí nastavení sady Visual Studio** | `true` |

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

### <a name="indentation-options"></a>Volby odsazení

Tato pravidla formátování se týkají použití odsazení k formátování kódu.

Příklad souboru *.editorconfig:*

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharp_indent_case_contents"></a>costře\_odsazení\_case_contents

|||
|-|-|
| **Název pravidla** | csharp_indent_case_contents |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- Odsazení `switch` obsahu případu<br /><br />`false`- Obsah případu `switch` neodsouvají |
| **Výchozí nastavení sady Visual Studio** | `true` |

- Pokud je toto pravidlo nastaveno na **hodnotu true**, i.
- Pokud je toto pravidlo nastaveno na **hodnotu false**, d.

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

#### <a name="csharp_indent_switch_labels"></a>costře\_odsazení\_switch_labels

|||
|-|-|
| **Název pravidla** | csharp_indent_switch_labels |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- Odsazení `switch` štítků<br /><br />`false`- Neodsouvat `switch` popisky |
| **Výchozí nastavení sady Visual Studio** | `true` |

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

#### <a name="csharp_indent_labels"></a>csharp\_indent_labels

|||
|-|-|
| **Název pravidla** | csharp_indent_labels |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `flush_left`- Popisky jsou umístěny v levém sloupci<br /><br />`one_less_than_current`- Popisky jsou umístěny v jedné menší odsazení aktuálního kontextu.<br /><br />`no_change`- Popisky jsou umístěny ve stejné odrážce jako aktuální kontext. |
| **Výchozí nastavení sady Visual Studio** | `no_change` |

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

#### <a name="csharp_indent_block_contents"></a>csharp_indent_block_contents

|||
|-|-|
| **Název pravidla** | csharp_indent_block_contents |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true` - <br /><br />`false` -  |
| **Výchozí nastavení sady Visual Studio** | `true` |

Příklady kódu:

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_braces"></a>csharp_indent_braces

|||
|-|-|
| **Název pravidla** | csharp_indent_braces |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true` - <br /><br />`false` -  |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_case_contents_when_block"></a>csharp_indent_case_contents_when_block

|||
|-|-|
| **Název pravidla** | csharp_indent_case_contents_when_block |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true` - <br /><br />`false` -  |
| **Výchozí nastavení sady Visual Studio** | `true` |

Příklady kódu:

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a>Volby mezer

Tato pravidla formátování se týkají použití znaků mezer y pro formátování kódu.

Příklad souboru *.editorconfig:*

```ini
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharp_space_after_cast"></a>csharp\_\_prostor after_cast

|||
|-|-|
| **Název pravidla** | csharp_space_after_cast |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- Umístěte znak mezery mezi přetypátku a hodnotu.<br /><br />`false`- Odstraňte mezeru mezi přetypátkem a hodnotou |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a>csharp_space_after_keywords_in_control_flow_statements

|||
|-|-|
| **Název pravidla** | csharp_space_after_keywords_in_control_flow_statements |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- Umístěte znak mezery za klíčové slovo do `for` příkazu toku ovládacího prvku, jako je smyčka<br /><br />`false`- Odebrání mezery za klíčovým slovem `for` v příkazu toku ovládacího prvku, jako je smyčka |
| **Výchozí nastavení sady Visual Studio** | `true` |

Příklady kódu:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a>csharp_space_between_parentheses

|||
|-|-|
| **Název pravidla** | csharp_space_between_parentheses |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `control_flow_statements`- Umístěte mezeru mezi závorky příkazů toku řízení<br /><br />`expressions`- Umístěte mezeru mezi závorky výrazů<br /><br />`type_casts`- Umístěte mezeru mezi závorky v přetypových náhonech |
| **Výchozí nastavení sady Visual Studio** | `false` |

Pokud toto pravidlo vynechete `control_flow_statements` `expressions`nebo `type_casts`použijete jinou hodnotu než , , nebo , nastavení se nepoužije.

Příklady kódu:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a>csharp\_\_prostor\_\_před\_dvojtečkou v inheritance_clause

|||
|-|-|
| **Název pravidla** | csharp_space_before_colon_in_inheritance_clause |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.7 |
| **Hodnoty** | `true`- Umístěte znak mezery před dvojtečku pro základny nebo rozhraní v deklaraci typu<br /><br />`false`- Odstranit prostor před dvojtečkou pro základny nebo rozhraní v deklaraci typu |
| **Výchozí nastavení sady Visual Studio** | `true` |

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

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a>csharp\_\_prostor\_\_za\_dvojtečkou v inheritance_clause

|||
|-|-|
| **Název pravidla** | csharp_space_after_colon_in_inheritance_clause |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.7 |
| **Hodnoty** | `true`- Umístěte znak mezery za dvojtečku pro základny nebo rozhraní v deklaraci typu<br /><br />`false`- Odstranit prostor za dvojtečkou pro základny nebo rozhraní v deklaraci typu |
| **Výchozí nastavení sady Visual Studio** | `true` |

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

#### <a name="csharp_space_around_binary_operators"></a>csharp\_\_prostor\_kolem binary_operators

|||
|-|-|
| **Název pravidla** | csharp_space_around_binary_operators |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.7 |
| **Hodnoty** | `before_and_after`- Vložit mezeru před a za binární operátor<br /><br />`none`- Odstraňte mezery před a za binární operátor<br /><br />`ignore`- Ignorovat mezery kolem binárníoperátory |
| **Výchozí nastavení sady Visual Studio** | `before_and_after` |

Pokud toto pravidlo vynechete `before_and_after`nebo `none`použijete jinou hodnotu než , , nebo `ignore`, nastavení nebude použito.

Příklady kódu:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **Název pravidla** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- Umístěte znak mezery za počáteční závorku a před uzavírací závorku seznamu parametrů deklarace metody.<br /><br />`false`- Odstranění znaků mezer za počáteční závorkou a před uzávěrkou závorek seznamu parametrů deklarace metody |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **Název pravidla** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.7 |
| **Hodnoty** | `true`- Vložit mezeru v závorce seznamu prázdných parametrů pro deklaraci metody<br /><br />`false`- Odebrání místa v závorce seznamu prázdných parametrů pro deklaraci metody |
| **Výchozí nastavení sady Visual Studio** | `false` |

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

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a>csharp_space_between_method_declaration_name_and_open_parenthesis

|||
|-|-|
| **Název pravidla** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true`- Umístěte znak mezery mezi název metody a počáteční závorku v deklaraci metody<br /><br />`false`- Odstranit znaky mezery mezi názvem metody a počáteční závorkou v deklaraci metody |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **Název pravidla** | csharp_space_between_method_call_parameter_list_parentheses |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- Umístěte znak mezery za počáteční závorku a před uzavírací závorku volání metody<br /><br />`false`- Odstranění znaků mezer za počáteční závorkou a před uzávěrkou závorky volání metody |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **Název pravidla** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.7 |
| **Hodnoty** | `true`- Vložení mezery do prázdných závorek seznamu argumentů<br /><br />`false`- Odstranění místa v prázdných závorcích seznamu argumentů |
| **Výchozí nastavení sady Visual Studio** | `false` |

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

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **Název pravidla** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.7 |
| **Hodnoty** | `true`- Vložení mezery mezi název volání metody a počáteční závorky<br /><br />`false`- Odstranit mezeru mezi názvem volání metody a otevřenízávapoložkami |
| **Výchozí nastavení sady Visual Studio** | `false` |

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

#### <a name="csharp_space_after_comma"></a>csharp_space_after_comma

|||
|-|-|
| **Název pravidla** | csharp_space_after_comma |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true`- Vložit mezeru za čárku<br /><br />`false`- Odstraňte místo po čárce |
| **Výchozí nastavení sady Visual Studio** | `true` |

Příklady kódu:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a>csharp_space_before_comma

|||
|-|-|
| **Název pravidla** | csharp_space_before_comma |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true`- Vložit mezeru před čárkou<br /><br />`false`- Odstraňte místo před čárkou |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a>csharp_space_after_dot

|||
|-|-|
| **Název pravidla** | csharp_space_after_dot |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true`- Vložit mezeru za tečku<br /><br />`false`- Odstraňte místo po tečku |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a>csharp_space_before_dot

|||
|-|-|
| **Název pravidla** | csharp_space_before_dot |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true`- Vložte místo před tečku <br /><br />`false`- Odstraňte místo před tečkou |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a>csharp_space_after_semicolon_in_for_statement

|||
|-|-|
| **Název pravidla** | csharp_space_after_semicolon_in_for_statement |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true`- Vložit mezeru za `for` každý středník v příkazu<br /><br />`false`- Odstranit prostor po každém `for` středníku v příkazu |
| **Výchozí nastavení sady Visual Studio** | `true` |

Příklady kódu:

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a>csharp_space_before_semicolon_in_for_statement

|||
|-|-|
| **Název pravidla** | csharp_space_before_semicolon_in_for_statement |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true`- Vložit mezeru před `for` každý středník v příkazu <br /><br />`false`- Odstranit prostor před každým `for` středníkem v příkazu |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a>csharp_space_around_declaration_statements

|||
|-|-|
| **Název pravidla** | csharp_space_around_declaration_statements |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `ignore`- Neodstraňujte další mezery znaky v prohlášení příkazy<br /><br />`false`- Odstranit další mezery znaky v příkazech prohlášení |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a>csharp_space_before_open_square_brackets

|||
|-|-|
| **Název pravidla** | csharp_space_before_open_square_brackets |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true`- Vložte místo před otevřením hranatých závorek`[` <br /><br />`false`- Odstraňte prostor před otevřením hranaté závorky`[` |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a>csharp_space_between_empty_square_brackets

|||
|-|-|
| **Název pravidla** | csharp_space_between_empty_square_brackets |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true`- Vložte mezeru mezi prázdné hranaté závorky`[ ]` <br /><br />`false`- Odstraňte mezeru mezi prázdnými hranaté závorky`[]` |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a>csharp_space_between_square_brackets

|||
|-|-|
| **Název pravidla** | csharp_space_between_square_brackets |
| **Použitelné jazyky** | C# |
| **Hodnoty** | `true`- Vložte mezery znaky v neprázdných hranatých závorkách`[ 0 ]` <br /><br />`false`- Odstraňte mezery znaky v neprázdných hranatých závorkách`[0]` |
| **Výchozí nastavení sady Visual Studio** | `false` |

Příklady kódu:

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a>Možnosti obtékání

Tato pravidla formátování se týkají použití jednoho řádky versus samostatné řádky pro příkazy a bloky kódu.

Příklad souboru *.editorconfig:*

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a>csharp_preserve_single_line_statements

|||
|-|-|
| **Název pravidla** | csharp_preserve_single_line_statements |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- Leave prohlášení a prohlášení členů na stejném řádku<br /><br />`false`- Leave prohlášení a prohlášení členů na různých řádcích |
| **Výchozí nastavení sady Visual Studio** | `true` |

Příklady kódu:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a>csharp_preserve_single_line_blocks

|||
|-|-|
| **Název pravidla** | csharp_preserve_single_line_blocks |
| **Použitelné jazyky** | C# |
| **Zavedená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`- Opustit blok kódu na jednom řádku<br /><br />`false`- Ponechat blok kódu na samostatných řádcích |
| **Výchozí nastavení sady Visual Studio** | `true` |

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

## <a name="see-also"></a>Viz také

- [Konvence jazyka](editorconfig-language-conventions.md)
- [Zásady vytváření názvů](editorconfig-naming-conventions.md)
- [Nastavení konvence kódování .NET pro EditorConfig](editorconfig-code-style-settings-reference.md)
