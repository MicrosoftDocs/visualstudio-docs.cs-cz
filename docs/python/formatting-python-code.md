---
title: Formátování kódu Pythonu
description: Visual Studio může automaticky formátovat kód Python včetně mezer, příkazy, zabalení a komentáře.
ms.date: 10/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 452dc1104147e5b29dd38790cbfa726ad0de7b1f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052190"
---
# <a name="format-python-code"></a>Formátování kódu Pythonu

Visual Studio vám umožňuje rychle přeformátování kódu tak, aby odpovídaly předem nakonfigurované možnosti formátování.

- Formátovat výběr: vyberte **upravit** > **Upřesnit** > **výběr formátu** nebo stiskněte klávesu **Ctrl** + **E** > **F**.
- Formátovat celý soubor: vyberte **upravit** > **Upřesnit** > **formátovat dokument** nebo stiskněte klávesu **Ctrl** + **E** > **D**.

Možnosti se nastavují pomocí **nástroje** > **možnosti** > **textový Editor** > **Python**  >  **Formátování** a jeho vnořená karty. Je nutné vybrat **zobrazit všechna nastavení** pro tyto možnosti se zobrazí:

![Python v sadě Visual Studio možnosti formátování](media/options-editor-formatting.png)

Možnosti formátování ve výchozím nastavení jsou nastavené tak, aby odpovídaly nadmnožinu [průvodce správným stylem období 8](https://www.python.org/dev/peps/pep-0008/). **Obecné** kartu určuje při formátování se aplikuje; nastavení na třech kartách jsou popsány v tomto článku.

[Podpora Pythonu v sadě Visual Studio](installing-python-support-in-visual-studio.md) přidá také užitečné [ **vyplnit odstavec komentáře** ](#fill-comment-paragraph-command) příkaz **upravit**  >   **Pokročilé** nabídky, jak je popsáno v další části.

## <a name="spacing"></a>Mezery

**Mezery** ovládacích prvků, kde prostory se přidají nebo odebrán po různé jazykové konstrukce. Každá možnost má tři možné hodnoty:

- Vráceno: zajistí, že se použije mezery.
- Zrušeno: Odebere všechny mezery.
- Neurčitá: opustí, původní formátování na místě.

Příklady pro různé možnosti jsou k dispozici v následujících tabulkách:

| Možnost definice třídy | Zaškrtnuto | Vymazat |
| --- | --- | --- | 
| **Vložit mezeru mezi název třídy prohlášení a seznam základních tříd** | `class X (object): pass` | `class X(object): pass` | 
| **Vložit mezeru mezi kulaté závorky seznamu základních tříd** | `class X( object ): pass` | `class X(object): pass` |
| **Vložit mezeru mezi kulaté závorky seznamu prázdném** | `class X( ): pass` | `class X(): pass` |

<br/>

| Možnost definice funkce | Zaškrtnuto | Vymazat |
| --- | --- | --- |
| **Vložit mezeru mezi název funkce deklarace a seznam parametrů** | `def X (): pass` | `def X(): pass` | 
| **Vložit mezeru mezi kulaté závorky seznamu parametrů** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Vložit mezeru mezi kulaté závorky seznamu prázdný parametr** | `def X( ): pass` | `def X(): pass` |
| **Vložit mezery kolem '=' ve výchozích hodnotách parametrů** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **Vložit mezeru před a za návratové operátory poznámek** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Možnost operátory | Zaškrtnuto | Vymazat |
| --- | --- | --- |
| **Vložit mezery kolem binárních operátorů** | `a + b` | `a+b` |
| **Vložit mezery kolem přiřazení** | `a = b` | `a=b` |

<br/>

| Možnost výraz řádkování | Zaškrtnuto | Vymazat |
| --- | --- | --- |
| **Vložit mezeru mezi název funkce volání a seznam argumentů.** | `X ()` | `X()` |
| **Vložit mezeru mezi kulaté závorky prázdného seznamu argumentů** | `X( )` | `X()` |
| **Vložit mezeru mezi kulaté závorky seznamu argumentů** | `X( a, b )` | `X(a, b)` |
| **Vložit mezeru mezi kulaté závorky výrazu** | `( a )` | `(a)` |
| **Vložit mezeru mezi kulaté závorky prázdné řazené kolekci členů** | `( )` | `()` |
| **Vložit mezeru mezi kulaté závorky řazené kolekce členů** | `( a, b )` | `(a, b)` |
| **Vložit mezeru mezi kulaté prázdné hranaté závorky** | `[ ]` | `[]` |
| **Vložit mezery mezi hranaté závorky seznamů** | `[ a, b ]` | `[a, b]` |
| **Vložit mezeru před levou hranatou závorku** | `x [i]` | `x[i]` |
| **Vložit mezeru mezi hranaté závorky** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Příkazy

**Příkazy** možnosti řízení automatické přepisování různé příkazy do další Pythonic formuláře.

| Možnost | Před formátováním | Po naformátování |
| --- | --- | --- |
| **Umístit importované moduly na nový řádek** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Odebrat zbytečné středníky** | `x = 42;` | `x = 42` |
| **Umístit více příkazů na nových řádcích** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Zabalení

**Obtékání** umožňuje nastavit **maximální šířka komentáře** (výchozí hodnota je 80). Pokud **zabalit komentáře, které jsou moc široké** je nastavena možnost, sada Visual Studio přeformátuje komentáře, aby nedošlo k překročení tohoto maximální šířku.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Vyplnit odstavec komentáře příkaz

**Upravit** > **Advanced** > **lnit odstavec komentáře** (**Ctrl**+**E**  >  **P**) přeformátuje a formátuje text komentáře, kombinování krátké řádky společně a rozdělení dlouhá.

Příklad:

```python
# foo
# bar
# baz
```

změny:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

změny:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
