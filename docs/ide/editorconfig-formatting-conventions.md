---
title: Konvence formátování .NET pro EditorConfig
ms.date: 04/02/2020
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0490912683fd683398c89e8e69b62dd3824ee04b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533468"
---
# <a name="formatting-conventions"></a>Konvence formátování

Do těchto kategorií patří konvence formátování pro EditorConfig pro Visual Studio:

- [Nastavení formátování .NET](#net-formatting-settings)

- [Nastavení formátování C#](#c-formatting-settings)

## <a name="rule-format"></a>Formát pravidla

Pravidla pro konvence formátování mají následující formát:

`rule_name = value`

Pro mnoho pravidel zadáte buď `true` (preferovat tento styl), nebo `false` (nepreferovat tento styl) pro `value` . Pro jiná pravidla zadáte hodnotu, například `flush_left` nebo `before_and_after` , která popisuje, kdy a kde použít pravidlo. Neurčíte závažnost.

## <a name="net-formatting-settings"></a>Nastavení formátování .NET

Pravidla formátování v této části se vztahují na C# a Visual Basic kód.

- [Uspořádat direktivy using](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Uspořádat direktivy using

Tato pravidla formátování se týkají řazení a zobrazení `using` direktiv a `Imports` příkazů.

Příklad souboru *. editorconfig* :

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a>dotnet \_ Sort \_ System \_ directives_first

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_sort_system_directives_first |
| **Příslušné jazyky** | C# a Visual Basic |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`-Setřídit System. * `using` direktivy abecedně a umístit je před jiné direktivy using.<br /><br />`false`– Neumísťujte direktivy System. * `using` před jinými `using` direktivami. |

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

#### <a name="dotnet_separate_import_directive_groups"></a>dotnet \_ – \_ samostatné \_ skupiny importu direktiv \_

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | dotnet_separate_import_directive_groups |
| **Příslušné jazyky** | C# a Visual Basic |
| **Představená verze** | Visual Studio 2017 verze 15.5 |
| **Hodnoty** | `true`– Vložte prázdný řádek mezi `using` skupiny direktiv.<br /><br />`false`– Neumísťujte prázdný řádek mezi `using` skupiny direktiv. |

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

## <a name="c-formatting-settings"></a>Nastavení formátování C#

Pravidla formátování v této části se vztahují pouze na kód jazyka C#.

- [Možnosti nového řádku](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Možnosti odsazení](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
  - csharp_indent_block_contents
  - csharp_indent_braces
  - csharp_indent_case_contents_when_block
- [Možnosti mezer](#spacing-options)
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
- [Možnosti zalamování](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks
- [Použití možností direktivy](#using-directive-options) 
  - csharp_using_directive_placement

### <a name="new-line-options"></a>Možnosti pro nové řádky

Tato pravidla formátování se týkají použití nových řádků pro formátování kódu.

Příklad souboru *. editorconfig* :

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

#### <a name="csharp_new_line_before_open_brace"></a>CSharp \_ nový \_ řádek \_ před \_ open_brace

Toto pravidlo se týká toho, zda by měla být otevřená složená závorka `{` na stejném řádku jako předchozí kód, nebo na nový řádek. Pro toto pravidlo zadáte **všechny**, **žádné**nebo jeden nebo více elementů kódu, jako jsou **metody** nebo **vlastnosti**, které definují, kdy má být toto pravidlo použito. Chcete-li zadat více prvků kódu, oddělte je čárkou (,).

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_new_line_before_open_brace |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `all`-Vyžadovat, aby byly složené závorky na novém řádku pro všechny výrazy ("Allman" Style).<br /><br />`none`– Vyžaduje, aby byly složené závorky na stejném řádku pro všechny výrazy ("K&R").<br /><br />`accessors`, `anonymous_methods` ,,, `anonymous_types` `control_blocks` `events` , `indexers` , `lambdas` , `local_functions` , `methods` , `object_collection_array_initializers` , `properties` , `types` -Vyžadovat, aby byly složené závorky na novém řádku pro zadaný element kódu (styl "Allman"). |

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

#### <a name="csharp_new_line_before_else"></a>CSharp \_ nový \_ řádek \_ before_else

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_new_line_before_else |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`-Umístit `else` příkazy na nový řádek.<br /><br />`false`-Umístit `else` příkazy na stejný řádek. |

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

#### <a name="csharp_new_line_before_catch"></a>CSharp \_ nový \_ řádek \_ before_catch

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_new_line_before_catch |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`-Umístit `catch` příkazy na nový řádek.<br /><br />`false`-Umístit `catch` příkazy na stejný řádek. |

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

#### <a name="csharp_new_line_before_finally"></a>CSharp \_ nový \_ řádek \_ before_finally

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_new_line_before_finally |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`– Vyžaduje, `finally` aby příkazy byly na novém řádku za pravou složenou závorkou.<br /><br />`false`– Vyžaduje, `finally` aby příkazy byly na stejném řádku jako pravá složená závorka. |

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

#### <a name="csharp_new_line_before_members_in_object_initializers"></a>CSharp \_ nový \_ řádek \_ před \_ členy \_ v \_ object_initializers

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_new_line_before_members_in_object_initializers |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`– Vyžaduje, aby členové inicializátorů objektů byli na samostatných řádcích.<br /><br />`false`– Vyžaduje, aby se členové inicializátorů objektů na stejném řádku |

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

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a>CSharp \_ nový \_ řádek \_ před \_ členy \_ v \_ anonymous_types

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_new_line_before_members_in_anonymous_types |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`– Vyžaduje, aby členové anonymních typů byli na samostatných řádcích.<br /><br />`false`– Vyžaduje, aby byli členové anonymních typů na stejném řádku. |

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

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_new_line_between_query_expression_clauses |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`– Vyžaduje, aby elementy klauzulí výrazů dotazu byly na samostatných řádcích.<br /><br />`false`– Vyžaduje, aby elementy klauzulí výrazů dotazu byly na stejném řádku. |

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

### <a name="indentation-options"></a>Možnosti odsazení

Tato pravidla formátování se týkají použití odsazení k formátování kódu.

Příklad souboru *. editorconfig* :

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

#### <a name="csharp_indent_case_contents"></a>CSharp \_ odsazení \_ case_contents

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_indent_case_contents |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`-Odsadit `switch` obsah Case<br /><br />`false`– Nesazovat `switch` obsah Case |

- Když je toto pravidlo nastavené na **true**, i.
- Když je toto pravidlo nastavené na **false**, d.

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

#### <a name="csharp_indent_switch_labels"></a>CSharp \_ odsazení \_ switch_labels

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_indent_switch_labels |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`– `switch` Popisky odsazení<br /><br />`false`– Nesazovat `switch` popisky |

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

#### <a name="csharp_indent_labels"></a>CSharp \_ indent_labels

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_indent_labels |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `flush_left`-Popisky jsou umístěné v levém sloupci.<br /><br />`one_less_than_current`-Popisky jsou umístěné v jednom odsazení k aktuálnímu kontextu.<br /><br />`no_change`-Popisky jsou umístěné ve stejné odsazení jako aktuální kontext. |

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

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_indent_block_contents |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` - <br /><br />`false` -  |

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

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_indent_braces |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` - <br /><br />`false` -  |

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

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_indent_case_contents_when_block |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` - <br /><br />`false` -  |

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

### <a name="spacing-options"></a>Možnosti mezer

Tato pravidla formátování se týkají použití znaků mezer k formátování kódu.

Příklad souboru *. editorconfig* :

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

#### <a name="csharp_space_after_cast"></a>CSharp \_ místo \_ after_cast

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_after_cast |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`-Umístit znak mezery mezi přetypování a hodnotu<br /><br />`false`-Odebrat mezeru mezi přetypováním a hodnotou |

Příklady kódu:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a>csharp_space_after_keywords_in_control_flow_statements

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_after_keywords_in_control_flow_statements |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`-Umístit znak mezery za klíčové slovo v příkazu toku řízení, jako je například `for` smyčka<br /><br />`false`-Odebrat mezeru za klíčovým slovem v příkazu toku řízení, jako je například `for` smyčka |

Příklady kódu:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a>csharp_space_between_parentheses

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_between_parentheses |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `control_flow_statements`-Umístit mezeru mezi závorky příkazů toku řízení<br /><br />`expressions`– Umístit mezeru mezi kulaté závorky výrazů<br /><br />`type_casts`– Místo mezi závorkami v přetypováních typů |

Pokud toto pravidlo vynecháte nebo použijete jinou hodnotu než `control_flow_statements` , `expressions` nebo `type_casts` , nastavení se nepoužije.

Příklady kódu:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a>CSharp \_ mezeru \_ před \_ dvojtečku \_ v \_ inheritance_clause

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_before_colon_in_inheritance_clause |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.7 |
| **Hodnoty** | `true`-Umístit znak mezery před dvojtečku pro základy nebo rozhraní v deklaraci typu<br /><br />`false`-Odebrat mezeru před dvojtečkou pro základy nebo rozhraní v deklaraci typu |

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

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a>CSharp \_ mezera \_ za \_ dvojtečkou \_ v \_ inheritance_clause

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_after_colon_in_inheritance_clause |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.7 |
| **Hodnoty** | `true`-Umístit znak mezery za dvojtečku pro základy nebo rozhraní v deklaraci typu<br /><br />`false`-Odebrat mezeru za dvojtečkou pro základy nebo rozhraní v deklaraci typu |

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

#### <a name="csharp_space_around_binary_operators"></a>CSharp \_ místo \_ kolem \_ binary_operators

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_around_binary_operators |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.7 |
| **Hodnoty** | `before_and_after`-Vložit mezeru před a za binární operátor<br /><br />`none`-Odebrat mezery před a za binárním operátorem<br /><br />`ignore`-Ignorovat mezery kolem binárních operátorů |

Pokud toto pravidlo vynecháte nebo použijete jinou hodnotu než `before_and_after` , `none` nebo `ignore` , nastavení se nepoužije.

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

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`– Vložte mezeru za levou (otevírací) závorku a před pravou (uzavírací) závorku seznamu parametrů deklarace metody.<br /><br />`false`-Odebrání znaků mezer za levou (otevírací) závorku a před pravou závorkou seznamu parametrů deklarace metody |

Příklady kódu:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.7 |
| **Hodnoty** | `true`-Vložit mezeru mezi závorky v seznamu prázdných parametrů pro deklaraci metody<br /><br />`false`– Odebrat místo v rámci prázdných závorek seznamu parametrů pro deklaraci metody |

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

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true`-Umístit znak mezery mezi název metody a levou závorku v deklaraci metody<br /><br />`false`-Odebrání znaků mezery mezi názvem metody a levou závorkou v deklaraci metody |

Příklady kódu:

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_between_method_call_parameter_list_parentheses |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`-Umístit mezeru za levou (otevírací) závorku a před pravou (uzavírací) závorku volání metody<br /><br />`false`-Odebrání znaků mezer za levou (otevírací) a před pravou (uzavírací) závorku volání metody |

Příklady kódu:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.7 |
| **Hodnoty** | `true`-Vložit mezeru mezi závorky v prázdném seznamu argumentů<br /><br />`false`-Odebrat mezeru v závorkách v prázdném seznamu argumentů |

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

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.7 |
| **Hodnoty** | `true`-Vložit mezeru mezi název volání metody a levou (otevírací) závorku<br /><br />`false`-Odebrat mezeru mezi názvem volání metody a levou závorkou |

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

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_after_comma |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true`-Vložit mezeru za čárku<br /><br />`false`-Odebrat mezeru za čárkou |

Příklady kódu:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a>csharp_space_before_comma

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_before_comma |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true`-Vložit mezeru před čárku<br /><br />`false`-Odebrat mezeru před čárkou |

Příklady kódu:

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a>csharp_space_after_dot

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_after_dot |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true`-Vložit mezeru za tečku<br /><br />`false`-Odebrat mezeru za tečkou |

Příklady kódu:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a>csharp_space_before_dot

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_before_dot |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true`-Vložit mezeru před tečku <br /><br />`false`-Odebrat mezeru před tečkou |

Příklady kódu:

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a>csharp_space_after_semicolon_in_for_statement

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_after_semicolon_in_for_statement |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true`-Vložit mezeru za každý středník v `for` příkazu<br /><br />`false`-Odebrat mezeru za každým středníkem v `for` příkazu |

Příklady kódu:

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a>csharp_space_before_semicolon_in_for_statement

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_before_semicolon_in_for_statement |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true`-Vložit mezeru před každý středník v `for` příkazu <br /><br />`false`-Odebrat mezeru před každým středníkem v `for` příkazu |

Příklady kódu:

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a>csharp_space_around_declaration_statements

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_around_declaration_statements |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `ignore`– V příkazech deklarací neodstraňujte nadbytečné znaky mezer.<br /><br />`false`-Odebrat nadbytečné znaky mezery v deklaracích deklarací |

Příklady kódu:

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a>csharp_space_before_open_square_brackets

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_before_open_square_brackets |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true`-Vložit mezeru před levou hranatou závorku`[` <br /><br />`false`-Odebrat mezeru před levou hranatou závorkou`[` |

Příklady kódu:

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a>csharp_space_between_empty_square_brackets

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_between_empty_square_brackets |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true`-Vložit mezeru mezi prázdné hranaté závorky`[ ]` <br /><br />`false`-Odstranit mezeru mezi prázdnými hranatými závorkami`[]` |

Příklady kódu:

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a>csharp_space_between_square_brackets

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_space_between_square_brackets |
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true`– Vkládat znaky mezer v neprázdných hranatých závorkách`[ 0 ]` <br /><br />`false`-Odebrat znaky mezery v neprázdných hranatých závorkách`[0]` |

Příklady kódu:

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a>Možnosti zalamování

Tato pravidla formátování se týkají použití jednoho řádku oproti samostatným řádkům pro příkazy a bloky kódu.

Příklad souboru *. editorconfig* :

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a>csharp_preserve_single_line_statements

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_preserve_single_line_statements |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`-Ponechat příkazy a deklarace členů na stejném řádku<br /><br />`false`-Opustit příkazy a deklarace členů na různých řádcích |

Příklady kódu:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a>csharp_preserve_single_line_blocks

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_preserve_single_line_blocks |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15.3 |
| **Hodnoty** | `true`-Ponechat blok kódu na jednom řádku<br /><br />`false`-Ponechat blok kódu na samostatných řádcích |

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

### <a name="using-directive-options"></a>Použití možností direktivy

Toto pravidlo formátování se týká použití direktiv použití direktivy umístěných uvnitř versus mimo obor názvů.

Příklad souboru *. editorconfig* :

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a>csharp_using_directive_placement

|Vlastnost|Hodnota|
|-|-|
| **Název pravidla** | csharp_using_directive_placement |
| **Příslušné jazyky** | C# |
| **Představená verze** |  Visual Studio 2019 verze 16.1 |
| **Hodnoty** | `outside_namespace`-Opustit direktivy using mimo obor názvů<br /><br />`inside_namespace`-Opustit direktivy using v oboru názvů |

Příklady kódu:

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{

}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
}
```

## <a name="see-also"></a>Viz také

- [Konvence jazyka](editorconfig-language-conventions.md)
- [Zásady vytváření názvů](editorconfig-naming-conventions.md)
- [Nastavení konvence kódování .NET pro EditorConfig](editorconfig-code-style-settings-reference.md)
