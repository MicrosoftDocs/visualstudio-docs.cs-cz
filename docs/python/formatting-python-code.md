---
title: Formátování kódu Pythonu
description: Visual Studio může automaticky přeformátovat kód Pythonu, včetně mezer, příkazů, zalamování a komentářů.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7b03e99a70edd587c9dfe2a43d326a64d14b9193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887884"
---
# <a name="format-python-code"></a>Formátování kódu Pythonu

Visual Studio umožňuje rychle přeformátovat kód tak, aby odpovídal předem nakonfigurovaným možnostem formátování.

- Formátování výběru: vyberte **Upravit**  >  **Rozšířené**  >  **Výběr formátu** nebo stiskněte **CTRL** + **E**  >  **F**.
- Chcete-li naformátovat celý soubor: vyberte **Upravit**  >  **Rozšířené**  >  **formátování dokumentu** nebo stiskněte klávesovou **zkratku CTRL** + **E**  >  **D**.

Možnosti jsou nastaveny prostřednictvím   >  **možností** nástroje  >  **textový editor**  >  **Python**  >  **formátování** a jeho vnořené karty. Musíte vybrat **Zobrazit všechna nastavení** , která se zobrazí pro tyto možnosti:

![Možnosti formátování Pythonu v aplikaci Visual Studio](media/options-editor-formatting.png)

Možnosti formátování ve výchozím nastavení jsou nastavené tak, aby odpovídaly nadmnožině [Průvodce stylem PEP 8](https://www.python.org/dev/peps/pep-0008/). Karta **Obecné** určuje, kdy se používá formátování; nastavení dalších tří karet jsou popsána v tomto článku.

[Podpora Pythonu v aplikaci Visual Studio](installing-python-support-in-visual-studio.md) také přidá do nabídky **Upravit** upřesnění užitečný příkaz k [**zadání komentáře k vyplňování**](#fill-comment-paragraph-command)  >   , jak je popsáno v další části.

## <a name="spacing"></a>Mezery

**Mezery mezi** ovládacími prvky, kde jsou vloženy nebo odebrány mezery kolem různých konstrukcí jazyka. Každá možnost má tři možné hodnoty:

- Checked: zajistí, že se mezery aplikují.
- Smazáno: Odebere všechny mezery.
- Neurčité: ponechá původní formátování na místě.

Příklady různých možností jsou k dispozici v následujících tabulkách:

| Definice třídy – možnost | Zaškrtnuto | Vymazán |
| --- | --- | --- |
| **Vložit mezeru mezi název deklarace třídy a seznam základů** | `class X (object): pass` | `class X(object): pass` |
| **Vložit mezeru mezi závorky v seznamu základů** | `class X( object ): pass` | `class X(object): pass` |
| **Vložit mezeru mezi závorky v prázdném seznamu základních tříd** | `class X( ): pass` | `class X(): pass` |

<br/>

| Možnost definice funkcí | Zaškrtnuto | Vymazán |
| --- | --- | --- |
| **Vložit mezeru mezi název a seznam parametrů deklarace funkce** | `def X (): pass` | `def X(): pass` |
| **Vložit mezeru mezi kulaté závorky seznamu parametrů** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Vložit mezeru mezi závorky v prázdném seznamu parametrů** | `def X( ): pass` | `def X(): pass` |
| **Vložit mezery kolem: ' = ' ve výchozích hodnotách parametrů** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **Vložit mezeru před a za návratové operátory poznámek** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Option Operators – možnost | Zaškrtnuto | Vymazán |
| --- | --- | --- |
| **Vložit mezery kolem binárních operátorů** | `a + b` | `a+b` |
| **Vložit mezery kolem přiřazení** | `a = b` | `a=b` |

<br/>

| Možnost řádkování výrazů | Zaškrtnuto | Vymazán |
| --- | --- | --- |
| **Vložit mezeru mezi název volání funkce a seznam argumentů** | `X ()` | `X()` |
| **Vložit mezeru mezi závorky v prázdném seznamu argumentů** | `X( )` | `X()` |
| **Vložit mezeru mezi kulaté závorky seznamu argumentů** | `X( a, b )` | `X(a, b)` |
| **Vložit mezeru mezi kulaté závorky výrazu** | `( a )` | `(a)` |
| **Vložit mezeru mezi závorky v prázdné řazené kolekci** | `( )` | `()` |
| **Vložit mezeru mezi závorky v řazené kolekci** | `( a, b )` | `(a, b)` |
| **Vložit mezeru mezi prázdné hranaté závorky** | `[ ]` | `[]` |
| **Vložit mezery mezi hranaté závorky seznamů** | `[ a, b ]` | `[a, b]` |
| **Vložit mezeru před levou hranatou závorku** | `x [i]` | `x[i]` |
| **Vložit mezeru mezi hranaté závorky** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Příkazy

Možnosti **příkazů** řídí automatické přepsání různých příkazů do dalších forem Pythonu.

| Možnost | Před formátováním | Po formátování |
| --- | --- | --- |
| **Umístit importované moduly na nový řádek** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Odebrat nepotřebné středníky** | `x = 42;` | `x = 42` |
| **Umístit více příkazů na nové řádky** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Tékající

Při **zalamování** lze nastavit **maximální šířku komentáře** (výchozí hodnota je 80). Pokud jsou nastavené **příliš široké** možnosti, sada Visual Studio přeformátuje komentáře tak, aby nepřesáhly maximální šířku.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Vyplnit komentář – příkaz odstavce

**Upravit**  >  **Rozšířené možnosti**  >  **Vyplní odstavec komentáře** (**CTRL +** +   >  **P**) přetéká a formátuje text komentáře, kombinuje krátké řádky dohromady a rozbalí dlouhé.

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
