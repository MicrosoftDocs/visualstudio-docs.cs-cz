---
title: Konvence formátování C++ EditorConfig
titleSuffix: ''
description: Přečtěte si, jak používat EditorConfig ke zformátování kódu C++ v aplikaci Visual Studio.
ms.date: 9/14/2020
author: jureid
ms.author: jureid
manager: jillfra
dev_langs:
- CPP
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- cplusplus
monikerRange: vs-2019
ms.openlocfilehash: f248ede6a4bb45a58d64a346489124462f304a86
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518541"
---
# <a name="c-editorconfig-formatting-conventions"></a>Konvence formátování C++ EditorConfig

Formátovací modul Visual Studio C++ má bohatou sadu konfigurovatelných nastavení, která se dají použít globálně. Chcete-li nastavit nastavení formátování C++ pro konkrétní pracovní prostor, použijte [clangformat](https://clang.llvm.org/docs/ClangFormat.html) nebo [EditorConfig](https://editorconfig.org/). Visual Studio i Visual Studio Code mají integrovanou podporu EditorConfig pro každé z globálních nastavení formátování sady Visual Studio C++, přičemž nastavení EditorConfig mají přednost. To znamená, že do svého pracovního prostoru můžete přidat soubory EditorConfig, abyste mohli konfigurovat formátování C++ na podrobnější úrovni a vynutili konzistentní styl kódu pro každého přispívajícího k projektu.

## <a name="c-formatting-conventions"></a>Konvence formátování C++

Nastavení EditorConfig formátování v jazyce C++ jsou předponou `cpp_` . Tady je příklad toho, jak může váš soubor EditorConfig vypadat takto:

```ini
[*.{c++,cc,cpp,cxx,h,h++,hh,hpp,hxx,inl,ipp,tlh,tli}]

cpp_indent_case_contents_when_block = true
cpp_new_line_before_open_brace_namespace = same_line
```

Zbývající část tohoto dokumentu obsahuje všechna nastavení formátování EditorConfig C++ podporovaná aplikací Visual Studio a VS Code.

### <a name="indentation-settings"></a>Nastavení odsazení

**Odsadit složené závorky**

- Název: `cpp_indent_braces`
- Hodnoty: `true` , `false`

**Odsadit každý řádek relativně k**

- Název: `cpp_indent_multi_line_relative_to`
- Hodnoty:
  - `outermost_parenthesis` – Při zadání nového řádku se tento řádek odsadí relativně k pravé závorce.
  - `innermost_parenthesis` – Při zadání nového řádku se tento řádek odsadí relativně k nejvnitřnější závorce.
  - `statement_begin` – Při zadání nového řádku se tento řádek odsadí relativně k začátku aktuálního příkazu.

**V závorkách zarovnejte nové řádky při jejich zadávání**

- Název: `cpp_indent_within_parentheses`
- Hodnoty:
  - `align_to_parenthesis` – Zarovná obsah k otevírací závorce.
  - `indent` – Odsadí nové řádky.

**V existujícím kódu nepoužívejte nastavení pro zarovnání nových řádků v závorkách.**

- Název: `cpp_indent_preserve_within_parentheses`
- Hodnoty: `true` , `false`

**Odsadit obsah Case**

- Název: `cpp_indent_case_contents`
- Hodnoty: `true` , `false`

**Odsadit popisky case**

- Název: `cpp_indent_case_labels`
- Hodnoty: `true` , `false`

**Odsadit závorky po příkazu case**

- Název: `cpp_indent_case_contents_when_block`
- Hodnoty: `true` , `false`

**Odsadit složené závorky výrazů lambda použitých jako parametry**

- Název: `cpp_indent_lambda_braces_when_parameter`
- Hodnoty: `true` , `false`

**Pozice popisků příkazu goto**

- Název: `cpp_indent_goto_labels`
- Hodnoty:
  - `one_left` – Jedno odsazení doleva
  - `leftmost_column` – Přesunout do sloupce úplně vlevo
  - `none` -Nechat odsazené

**Pozice direktiv preprocesoru**

- Název: `cpp_indent_preprocessor`
- Hodnoty:
  - `one_left` – Jedno odsazení doleva
  - `leftmost_column` – Přesunout do sloupce úplně vlevo
  - `none` -Nechat odsazené

**Odsadit specifikátory přístupu**

- Název: `cpp_indent_access_specifiers`
- Hodnoty: `true` , `false`

**Odsadit obsah oboru názvů**

- Název: `cpp_indent_namespace_contents`
- Hodnoty: `true` , `false`

**Zachovat odsazení komentářů**

- Název: `cpp_indent_preserve_comments`
- Hodnoty: `true` , `false`

### <a name="newline-settings"></a>Nastavení nového řádku

**Pozice otevřených složených závorek pro obory názvů**

- Název: `cpp_new_line_before_open_brace_namespace`
- Hodnoty:
  - `new_line` -Přesunout na nový řádek
  - `same_line` -Zachovat na stejném řádku, ale přidat mezeru před
  - `ignore` – Bez automatického přemístění

**Pozice levých složených závorek pro typy**

- Název: `cpp_new_line_before_open_brace_type`
- Hodnoty:
  - `new_line` -Přesunout na nový řádek
  - `same_line` -Zachovat na stejném řádku, ale přidat mezeru před
  - `ignore` – Bez automatického přemístění

**Pozice otevřených složených závorek pro funkce**

- Název: `cpp_new_line_before_open_brace_function`
- Hodnoty:
  - `new_line` -Přesunout na nový řádek
  - `same_line` -Zachovat na stejném řádku, ale přidat mezeru před
  - `ignore` – Bez automatického přemístění

**Pozice otevřených složených závorek pro řídicí bloky**

- Název: `cpp_new_line_before_open_brace_block`
- Hodnoty:
  - `new_line` -Přesunout na nový řádek
  - `same_line` -Zachovat na stejném řádku, ale přidat mezeru před
  - `ignore` – Bez automatického přemístění

**Pozice otevřených složených závorek pro výrazy lambda**

- Název: `cpp_new_line_before_open_brace_lambda`
- Hodnoty:
  - `new_line` -Přesunout na nový řádek
  - `same_line` -Zachovat na stejném řádku, ale přidat mezeru před
  - `ignore` – Bez automatického přemístění
 
**Umístit složené závorky oboru na samostatné řádky**

- Název: `cpp_new_line_scope_braces_on_separate_lines`
- Hodnoty: `true` , `false`

**Pro prázdné typy přesuňte uzavírací závorky na stejný řádek jako levou složenou závorku.**

- Název: `cpp_new_line_close_brace_same_line_empty_type`
- Hodnoty: `true` , `false`

**Pro prázdné tělo funkcí přesuňte uzavírací závorky na stejný řádek jako levou složenou závorku.**

- Název: `cpp_new_line_close_brace_same_line_empty_function`
- Hodnoty: `true` , `false`

**Umístit klíčové slovo Catch a podobná klíčová slova na nový řádek**

- Název: `cpp_new_line_before_catch`
- Hodnoty: `true` , `false`

**Umístit else na nový řádek**

- Název: `cpp_new_line_before_else`
- Hodnoty: `true` , `false`

**Umístit while ve smyčce do-while na nový řádek**

- Název: `cpp_new_line_before_while_in_do_while`
- Hodnoty: `true` , `false`

### <a name="spacing-settings"></a>Nastavení mezer

**Mezery mezi názvy funkcí a levou závorkou seznamů argumentů**

- Název: `cpp_space_before_function_open_parenthesis`
- Hodnoty:
  - `insert` -Vložit mezeru
  - `remove` -Odebrat mezery
  - `ignore` – Neměňte mezery

**Vložit mezeru mezi kulaté závorky seznamu argumentů**

- `cpp_space_within_parameter_list_parentheses`Hodnoty názvu: `true` ,`false`

**Vložit mezeru mezi kulaté závorky, pokud je seznam argumentů prázdný**

- Název: `cpp_space_between_empty_parameter_list_parentheses`
- Hodnoty: `true` , `false`

**Vložit mezeru mezi klíčové slovo a levou závorku v příkazech toku ovládacích prvků**

- Název: `cpp_space_after_keywords_in_control_flow_statements`
- Hodnoty: `true` , `false`

**Vložit mezeru mezi závorky příkazu ovládacího prvku**

- Název: `cpp_space_within_control_flow_statement_parentheses`
- Hodnoty: `true` , `false`

**Vložit mezeru před levou závorku seznamů argumentů lambda**

- Název: `cpp_space_before_lambda_open_parenthesis`
- Hodnoty: `true` , `false`

**Vložit mezeru mezi kulaté závorky přetypování C-Style**

- Název: `cpp_space_within_cast_parentheses`
- Hodnoty: `true` , `false`

**Vložit mezeru za pravou závorku přetypování C-Style**

- Název: `cpp_space_after_cast_close_parenthesis`
- Hodnoty: `true` , `false`

**Vložit mezeru do závorek výrazu v závorkách**

- Název: `cpp_space_within_expression_parentheses`
- Hodnoty: `true` , `false`

**Vložit mezeru před levou složenou závorku bloků**

- Název: `cpp_space_before_block_open_brace`
- Hodnoty: `true` , `false`

**Vložit mezeru mezi prázdné složené závorky**

- Název: `cpp_space_between_empty_braces`
- Hodnoty: `true` , `false`

**Vložit mezeru před levou závorku jednotné inicializace a seznamů inicializátorů**

- Název: `cpp_space_before_initializer_list_open_brace`
- Hodnoty: `true` , `false`

**Vložit mezeru do složených závorek jednotné inicializace a seznamů inicializátorů**

- Název: `cpp_space_within_initializer_list_braces`
- Hodnoty: `true` , `false`

**Zachovat mezery uvnitř jednotné inicializace a seznamů inicializátorů**

- Název: `cpp_space_preserve_in_initializer_list`
- Hodnoty: `true` , `false`

**Vložit mezeru před levou hranatou závorku**

- Název: `cpp_space_before_open_square_bracket`
- Hodnoty: `true` , `false`

**Vložit mezeru mezi hranaté závorky**

- Název: `cpp_space_within_square_brackets`
- Hodnoty: `true` , `false`

**Vložit mezeru před prázdné hranaté závorky**

- Název: `cpp_space_before_empty_square_brackets`
- Hodnoty: `true` , `false`

**Vložit mezeru mezi prázdné hranaté závorky**

- Název: `cpp_space_between_empty_square_brackets`
- Hodnoty: `true` , `false`

**Seskupit hranaté závorky u multidimenzionálních polí dohromady**

- Název: `cpp_space_group_square_brackets`
- Hodnoty: `true` , `false`

**Vložit mezeru do hranatých závorek pro lambda**

- Název: `cpp_space_within_lambda_brackets`
- Hodnoty: `true` , `false`

**SpaceBetweenEmptyLambdaBrackets**

- Název: `cpp_space_between_empty_lambda_brackets`
- Hodnoty: `true` , `false`

**Vložit mezeru před čárky**

- Název: `cpp_space_before_comma`
- Hodnoty: `true` , `false`

**Vložit mezeru za čárky**

- Název: `cpp_space_after_comma`
- Hodnoty: `true` , `false`

**Odebrat mezery před a za členské operátory**

- Název: `cpp_space_remove_around_member_operators`
- Hodnoty: `true` , `false`

**Vložit mezeru před dvojtečku pro základ v deklaracích typů**

- Název: `cpp_space_before_inheritance_colon`
- Hodnoty: `true` , `false`

**Vložit mezeru před dvojtečku pro konstruktory**

- Název: `cpp_space_before_constructor_colon`
- Hodnoty: `true` , `false`

**Odebrat mezeru před středníky**

- Název: `cpp_space_remove_before_semicolon`
- Hodnoty: `true` , `false`

**Vložit mezeru za středníky**

- Název: `cpp_space_after_semicolon`
- Hodnoty: `true` , `false`

**Odebrat mezery mezi unárními operátory a jejich operandy**

- Název: `cpp_space_remove_around_unary_operator`
- Hodnoty: `true` , `false`

**Mezery pro binární operátory**

- Název: `cpp_space_around_binary_operator`
- Hodnoty:
  - `insert` -Vložit mezery před a za binární operátory.
  - `remove` – Odeberte mezery kolem binárních operátorů.
  - `ignore` – Neměňte mezery kolem binárních operátorů.

**Mezery pro operátory přiřazení**

- Název: `cpp_space_around_assignment_operator`
- Hodnoty:
  - `insert` – Vložte mezery kolem operátorů přiřazení.
  - `remove` – Odebrat mezery kolem operátorů přiřazení.
  - `ignore` – Neměňte mezery kolem operátorů přiřazení.

**Zarovnání ukazatele na odkaz**

- Název: `cpp_space_pointer_reference_alignment`
- Hodnoty:
  - `left` -Zarovnat doleva.
  - `center` – Zarovnat na střed
  - `right` -Zarovnat vpravo.
  - `ignore` – Nechte beze změny.

**Mezery pro podmíněné operátory**

- Název: `cpp_space_around_ternary_operator`
- Hodnoty:
  - `insert` – Vložte mezery kolem podmíněných operátorů.
  - `remove` – Odeberte mezery kolem podmíněných operátorů.
  - `ignore` – Neměňte mezery kolem podmíněných operátorů.

### <a name="wrapping-options"></a>Možnosti zalamování

**Možnosti zalamování pro bloky**

- Název: `cpp_wrap_preserve_blocks`
- Hodnoty:
  - `one_liners` – Nezalomí jednořádkový blok kódu.
  - `all_one_line_scopes` – Nezalamovat bloky kódu, ve kterých jsou levou a pravou závorku na dalším řádku.
  - `never` -Vždy použít nastavení nových řádků pro bloky.

## <a name="see-also"></a>Viz také:

- [EditorConfig.org](https://editorconfig.org/)
- [Podpora EditorConfig pro službu jazyka](../extensibility/supporting-editorconfig.md)
- [Funkce editoru kódu](writing-code-in-the-code-and-text-editor.md)
