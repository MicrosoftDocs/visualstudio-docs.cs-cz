---
title: Konvence formátování .NET pro EditorConfig
ms.date: 07/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 42f1ab99a82f402ef6eced09ad5e47cf54122b86
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652792"
---
# <a name="formatting-conventions"></a>Konvence formátování

Do těchto kategorií patří konvence formátování pro EditorConfig pro Visual Studio:

- [Nastavení formátování .NET](#net-formatting-settings)

- [C#nastavení formátování](#c-formatting-settings)

## <a name="rule-format"></a>Formát pravidla

Pravidla pro konvence formátování mají následující formát:

`rule_name = value`

Pro mnoho pravidel zadáte buď `true` (preferovat tento styl), nebo `false` (nedoporučujeme tento styl) pro `value`. Pro jiná pravidla zadáte hodnotu, například `flush_left` nebo `before_and_after`, která popisuje, kdy a kde se má pravidlo použít. Neurčíte závažnost.

## <a name="net-formatting-settings"></a>Nastavení formátování .NET

Pravidla formátování v této části se vztahují na C# kód a Visual Basic.

- [Uspořádat direktivy using](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Uspořádat direktivy using

Tato pravidla formátování se týkají řazení a zobrazování direktiv `using` a příkazů `Imports`.

Příklad souboru *. editorconfig* :

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a>dotnet \_sort \_system \_directives_first

|||
|-|-|
| **Název pravidla** | dotnet_sort_system_directives_first |
| **Příslušné jazyky** | C# a Visual Basic |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `true` – Sorting System. * `using` direktivy abecedně a umístit je před jiné direktivy using.<br /><br />`false` – neumísťujte direktivy System. * `using` před jinými direktivami `using`. |
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

#### <a name="dotnet_separate_import_directive_groups"></a>dotnet \_separate \_import \_directive \_groups

|||
|-|-|
| **Název pravidla** | dotnet_separate_import_directive_groups |
| **Příslušné jazyky** | C# a Visual Basic |
| **Představená verze** | Visual Studio 2017 verze 15,5 |
| **Hodnoty** | `true` – vložte mezi skupiny direktiv `using` prázdný řádek.<br /><br />`false` – neumísťují prázdný řádek mezi skupiny direktiv `using`. |
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

## <a name="c-formatting-settings"></a>C#nastavení formátování

Pravidla formátování v této části se vztahují pouze na C# kód.

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

#### <a name="csharp_new_line_before_open_brace"></a>CSharp \_new \_line \_before \_open_brace

Toto pravidlo se týká, zda by měla být otevřená `{`a složené závorky na stejném řádku jako předchozí kód, nebo na nový řádek. Pro toto pravidlo zadáte **všechny**, **žádné**nebo jeden nebo více elementů kódu, jako jsou **metody** nebo **vlastnosti**, které definují, kdy má být toto pravidlo použito. Chcete-li zadat více prvků kódu, oddělte je čárkou (,).

|||
|-|-|
| **Název pravidla** | csharp_new_line_before_open_brace |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `all` – vyžaduje, aby byly složené závorky na novém řádku pro všechny výrazy ("Allman" stylu).<br /><br />`none` – vyžaduje, aby byly složené závorky na stejném řádku pro všechny výrazy ("K & R").<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers` 0 1 – vyžadují, aby byly složené závorky na novém řádku pro zadaný element kódu (Allman). |
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

#### <a name="csharp_new_line_before_else"></a>CSharp \_new \_line \_before_else

|||
|-|-|
| **Název pravidla** | csharp_new_line_before_else |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `else` příkazy `true` umístit na nový řádek.<br /><br />`else` příkazy `false` umístit na stejný řádek. |
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

#### <a name="csharp_new_line_before_catch"></a>CSharp \_new \_line \_before_catch

|||
|-|-|
| **Název pravidla** | csharp_new_line_before_catch |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `catch` příkazy `true` umístit na nový řádek.<br /><br />`catch` příkazy `false` umístit na stejný řádek. |
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

#### <a name="csharp_new_line_before_finally"></a>CSharp \_new \_line \_before_finally

|||
|-|-|
| **Název pravidla** | csharp_new_line_before_finally |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `true` – vyžaduje, aby byly příkazy `finally` na novém řádku za pravou závorkou.<br /><br />`false` – vyžaduje, aby příkazy `finally` byly na stejném řádku jako pravá složená závorka. |
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

#### <a name="csharp_new_line_before_members_in_object_initializers"></a>CSharp \_new \_line \_before \_members \_in \_object_initializers

|||
|-|-|
| **Název pravidla** | csharp_new_line_before_members_in_object_initializers |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `true` – vyžaduje, aby členové inicializátorů objektů byli na samostatných řádcích<br /><br />`false` – vyžaduje, aby členové inicializátorů objektů byli na stejném řádku |
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

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a>CSharp \_new \_line \_before \_members \_in \_anonymous_types

|||
|-|-|
| **Název pravidla** | csharp_new_line_before_members_in_anonymous_types |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `true` – vyžaduje, aby členové anonymních typů byli na samostatných řádcích<br /><br />`false` – vyžaduje, aby byli členové anonymních typů na stejném řádku. |
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
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `true` – vyžaduje, aby elementy klauzulí výrazů dotazu byly na samostatných řádcích.<br /><br />`false` – vyžaduje, aby elementy klauzule dotazu Expression byly na stejném řádku. |
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

#### <a name="csharp_indent_case_contents"></a>CSharp \_indent \_case_contents

|||
|-|-|
| **Název pravidla** | csharp_indent_case_contents |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `true` – odsazení obsahu `switch` případu<br /><br />`false` – nesazovat `switch` velikost písmen |
| **Výchozí nastavení sady Visual Studio** | `true` |

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

#### <a name="csharp_indent_switch_labels"></a>CSharp \_indent \_switch_labels

|||
|-|-|
| **Název pravidla** | csharp_indent_switch_labels |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | popisky `switch` `true`-odsazení<br /><br />`false` – nesazovat `switch` popisky |
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

#### <a name="csharp_indent_labels"></a>CSharp \_indent_labels

|||
|-|-|
| **Název pravidla** | csharp_indent_labels |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `flush_left` – popisky se umístí do sloupce úplně vlevo.<br /><br />`one_less_than_current` – popisky se umístí do aktuálního kontextu o jedno méně odsazení.<br /><br />`no_change` – popisky jsou umístěné ve stejné odsazení jako aktuální kontext. |
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
| **Příslušné jazyky** | C# |
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
| **Příslušné jazyky** | C# |
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
| **Příslušné jazyky** | C# |
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

#### <a name="csharp_space_after_cast"></a>CSharp \_space \_after_cast

|||
|-|-|
| **Název pravidla** | csharp_space_after_cast |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `true` – umístit znak mezery mezi přetypování a hodnotu<br /><br />`false` – odebere mezeru mezi přetypováním a hodnotou. |
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
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `true` – umístit znak mezery za klíčové slovo v příkazu toku řízení, jako je například smyčka `for`<br /><br />`false` – odebrat mezeru za klíčovým slovem v příkazu toku řízení, jako je například smyčka `for` |
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
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `control_flow_statements` – umístit mezeru mezi kulaté závorky příkazů toku řízení<br /><br />`expressions` – umístit mezeru mezi kulaté závorky výrazů<br /><br />místo mezi závorkami v přetypováních typů `type_casts` mezera |
| **Výchozí nastavení sady Visual Studio** | `false` |

Pokud toto pravidlo vynecháte nebo použijete jinou hodnotu než `control_flow_statements`, `expressions` nebo `type_casts`, nastavení se nepoužije.

Příklady kódu:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a>CSharp \_space \_before \_colon \_in \_inheritance_clause

|||
|-|-|
| **Název pravidla** | csharp_space_before_colon_in_inheritance_clause |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,7 |
| **Hodnoty** | `true` – umístit znak mezery před dvojtečku pro základy nebo rozhraní v deklaraci typu<br /><br />`false` – odebrání mezery před dvojtečkou pro základy nebo rozhraní v deklaraci typu |
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

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a>CSharp \_space \_after \_colon \_in \_inheritance_clause

|||
|-|-|
| **Název pravidla** | csharp_space_after_colon_in_inheritance_clause |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,7 |
| **Hodnoty** | `true` – umístit znak mezery za dvojtečku pro základny nebo rozhraní v deklaraci typu<br /><br />`false` – odebrání místa za dvojtečkou pro základny nebo rozhraní v deklaraci typu |
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

#### <a name="csharp_space_around_binary_operators"></a>CSharp \_space \_around \_binary_operators

|||
|-|-|
| **Název pravidla** | csharp_space_around_binary_operators |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,7 |
| **Hodnoty** | `before_and_after` – vložit mezeru před a za binární operátor<br /><br />`none` – odebrat mezery před a za binárním operátorem<br /><br />`ignore` – ignorovat mezery kolem binárních operátorů |
| **Výchozí nastavení sady Visual Studio** | `before_and_after` |

Pokud toto pravidlo vynecháte nebo použijete jinou hodnotu než `before_and_after`, `none` nebo `ignore`, nastavení se nepoužije.

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
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `true` – umístit znak mezery za levou (otevírací) závorku a před pravou (uzavírací) závorku seznamu parametrů deklarace<br /><br />`false` – odebrání znaků mezer za levou (otevírací) závorku a před pravou závorkou seznamu parametrů deklarace metody |
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
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,7 |
| **Hodnoty** | `true` – vložit mezeru mezi kulaté závorky v seznamu parametrů pro deklaraci metody<br /><br />`false` – odebrat místo v rámci prázdných závorek seznamu parametrů pro deklaraci metody |
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
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` – umístit znak mezery mezi název metody a levou závorku v deklaraci metody<br /><br />`false` – odebrání znaků mezer mezi názvem metody a levou závorkou v deklaraci metody |
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
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `true` – umístit znak mezery za levou (otevírací) závorku a před pravou (uzavírací) závorku volání metody<br /><br />`false` – odebrání znaků mezer za levou (otevírací) závorku a před pravou závorkou volání metody |
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
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,7 |
| **Hodnoty** | `true` – vložit mezeru mezi závorky v prázdném seznamu argumentů<br /><br />`false` – odebrat místo v rámci prázdných závorek seznamu argumentů |
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
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,7 |
| **Hodnoty** | `true` – vložit mezeru mezi název volání metody a levou (otevírací) závorku<br /><br />`false` – odebere mezeru mezi názvem volání metody a levou závorkou. |
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
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` – vložit mezeru za čárku<br /><br />`false` – odebrat mezeru za čárkou |
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
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` – vložit mezeru před čárku<br /><br />`false` – odebrat mezeru před čárkou |
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
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` – vložte mezeru za tečku<br /><br />`false` – odebrání mezery za tečkou |
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
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` – vložit mezeru před tečku <br /><br />`false` – odebrání mezery před tečkou |
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
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` – vložte mezeru za každý středník v příkazu `for`<br /><br />`false` – odebrat mezeru za každým středníkem v příkazu `for` |
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
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` – vložte mezeru před každý středník v příkazu `for` <br /><br />`false` – před každým středníkem v příkazu `for` odebrat mezeru. |
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
| **Příslušné jazyky** | C# |
| **Hodnoty** | `ignore` – v příkazech deklarace se neodstraňují nadbytečné znaky<br /><br />`false` – odebrání nadbytečného znaku mezery v deklaracích příkazů |
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
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` – vložte mezeru před levou hranatou závorku `[` <br /><br />`false` – před levou hranatou závorkou odebrat mezeru `[` |
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
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` – vložit mezeru mezi prázdné hranaté závorky `[ ]` <br /><br />`false` – odstranění mezery mezi prázdnými hranatými závorkami `[]` |
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
| **Příslušné jazyky** | C# |
| **Hodnoty** | `true` – vkládat znaky mezer v neprázdných hranatých závorkách `[ 0 ]` <br /><br />`false` – odebrání znaků mezery v neprázdných hranatých závorkách `[0]` |
| **Výchozí nastavení sady Visual Studio** | `false` |

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

|||
|-|-|
| **Název pravidla** | csharp_preserve_single_line_statements |
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | příkazy `true`-opustit a deklarace členů na stejném řádku<br /><br />příkazy `false`-opustit a deklarace členů na různých řádcích |
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
| **Příslušné jazyky** | C# |
| **Představená verze** | Visual Studio 2017 verze 15,3 |
| **Hodnoty** | `true`-ponechat blok kódu na jednom řádku<br /><br />`false`-ponechat blok kódu na samostatných řádcích |
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

## <a name="see-also"></a>Viz také:

- [Jazykové konvence](editorconfig-language-conventions.md)
- [Zásady vytváření názvů](editorconfig-naming-conventions.md)
- [Nastavení konvence kódování .NET pro EditorConfig](editorconfig-code-style-settings-reference.md)
