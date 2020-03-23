---
title: Formátování kódu Pythonu
description: Visual Studio můžete automaticky přeformátovat kód Pythonu, včetně mezery, příkazy, obtékání a komentáře.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6e95d05c3fbc0dd46d235c7480bd4a9caa48947e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957529"
---
# <a name="format-python-code"></a>Formátování kódu Pythonu

Visual Studio umožňuje rychle přeformátovat kód tak, aby odpovídal předkonfigurovaným možnostem formátování.

- Formátování výběru: vyberte **Upravit** > **rozšířený** > **výběr formátu** nebo stiskněte **Ctrl**+**E** > **F**.
- Formátování celého souboru: vyberte **Upravit** > **dokument v rozšířeném** > **formátu** nebo stiskněte **kombinaci kláves Ctrl**+**E** > **D**.

Možnosti jsou **nastaveny** > pomocí**možnosti** > nástroje**Text Editor** > **Python** > **formátování** a jeho vnořené karty. Chcete-li, aby se tyto možnosti zobrazily, musíte vybrat **možnost Zobrazit všechna nastavení:**

![Možnosti formátování pythonu v sadě Visual Studio](media/options-editor-formatting.png)

Možnosti formátování jsou ve výchozím nastavení nastaveny tak, aby odpovídaly nadsadě [průvodce stylem PEP 8](https://www.python.org/dev/peps/pep-0008/). Karta **Obecné** určuje, kdy je formátování použito. nastavení pro další tři karty jsou popsány v tomto článku.

[Podpora Pythonu v sadě Visual Studio](installing-python-support-in-visual-studio.md) také přidá užitečný příkaz [**Odstavec výplně**](#fill-comment-paragraph-command) do nabídky **Upravit** > **upřesnit,** jak je popsáno v novější části.

## <a name="spacing"></a>Mezery

**Rozteč** ovládací prvky, kde jsou mezery vloženy nebo odebrány kolem různých jazykových konstrukcí. Každá možnost má tři možné hodnoty:

- Zaškrtnuto: zajistí, že se použije mezera.
- Vymazáno: odstraní všechny mezery.
- Neurčitý: ponechá původní formátování na místě.

Příklady různých možností jsou uvedeny v následujících tabulkách:

| Definice tříd, volba | Zaškrtnuté | Vymazány |
| --- | --- | --- |
| **Vložení mezery mezi název deklarace třídy a seznam základů** | `class X (object): pass` | `class X(object): pass` |
| **Vložení mezery do závorek seznamu základů** | `class X( object ): pass` | `class X(object): pass` |
| **Vložení mezery do závorek seznamu prázdných základů** | `class X( ): pass` | `class X(): pass` |

<br/>

| Definice funkcí, volba | Zaškrtnuté | Vymazány |
| --- | --- | --- |
| **Vložení mezery mezi název deklarace funkce a seznam parametrů** | `def X (): pass` | `def X(): pass` |
| **Vložení mezery do závorek seznamu parametrů** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Vložení mezery do závorek seznamu prázdných parametrů** | `def X( ): pass` | `def X(): pass` |
| **Vložení mezer kolem '=' ve výchozích hodnotách parametrů** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **Vložení mezery před a po operátorech poznámky vrácení** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Možnost Operátory | Zaškrtnuté | Vymazány |
| --- | --- | --- |
| **Vložení mezer kolem binárních operátorů** | `a + b` | `a+b` |
| **Vložení mezer kolem přiřazení** | `a = b` | `a=b` |

<br/>

| Mezery mezi výrazy, volba | Zaškrtnuté | Vymazány |
| --- | --- | --- |
| **Vložení mezery mezi název volání funkce a seznam argumentů** | `X ()` | `X()` |
| **Vložení mezery do prázdných závorek seznamu argumentů** | `X( )` | `X()` |
| **Vložení mezery do závorek seznamu argumentů** | `X( a, b )` | `X(a, b)` |
| **Vložení mezery do závorek výrazu** | `( a )` | `(a)` |
| **Vložení mezery do prázdných závorek řazené kolekce členů** | `( )` | `()` |
| **Vložení mezery do závorek n-tice** | `( a, b )` | `(a, b)` |
| **Vložení místa do prázdných hranatých závorek** | `[ ]` | `[]` |
| **Vložení mezer mezi hranaté závorky seznamů** | `[ a, b ]` | `[a, b]` |
| **Vložení místa před otevřenou hranatou závorku** | `x [i]` | `x[i]` |
| **Vložení místa do hranatých závorek** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Příkazy

Možnosti **příkazy** řídí automatické přepisování různých příkazů do více pythonických formulářů.

| Možnost | Před formátováním | Po formátování |
| --- | --- | --- |
| **Umístění importovaných modulů na nový řádek** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Odebrání nepotřebných středníků** | `x = 42;` | `x = 42` |
| **Umístění více příkazů na nové řádky** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Obtékání

**Obtékání** umožňuje nastavit **maximální šířku komentáře** (výchozí hodnota je 80). Pokud **wrap komentáře, které jsou příliš široké** možnost, Visual Studio přeformátuje komentáře nepřesahující tuto maximální šířku.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Vyplnit komentář Odstavec, příkaz

**Upravit** > **advanced** > **fill komentář odstavec** (**Ctrl**+**E** > **P**) přeformátuje a formátuje text komentáře, kombinující krátké řádky dohromady a rozdělení dlouhé.

Například:

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
