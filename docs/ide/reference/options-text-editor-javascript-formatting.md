---
title: Možnosti, textový editor, JavaScript, formátování
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa846a25e1383c0c164dfb4747899f5e86237d32
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671050"
---
# <a name="options-text-editor-javascript-formatting"></a>Možnosti, textový editor, JavaScript, formátování
Použití **formátování** stránku **možnosti** dialogové okno Nastavení možností pro formátování kódu v editoru kódu. Pro přístup k této stránce, na panelu nabídek zvolte **nástroje**, **možnosti**a potom rozbalte **textový Editor**, **JavaScript**a **Formátování**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Automatické formátování
 Tyto možnosti určují, kdy dochází k formátování v **zdroj** zobrazení.

### <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

|Možnost|Popis|
|------------|-----------------|
|**Formátovat dokončený řádek při stisknutí klávesy Enter**|Pokud je vybraná tato možnost, Editor kódu automaticky naformátuje řádek, pokud zvolíte klávesu Enter.|
|**Formátovat dokončený příkaz při;**|Pokud je vybraná tato možnost, Editor kódu automaticky naformátuje řádek, pokud zvolíte klávesu středník.|
|**Otevřít formátovat blok při {**|Pokud je vybraná tato možnost, Editor kódu automaticky naformátuje řádek při výběru levou složenou závorku klíč.|
|**Formátovat dokončený ený blok při}**|Pokud je vybraná tato možnost, Editor kódu automaticky naformátuje řádek, pokud zvolíte uzavírací složenou závorku klíč.|
|**Formátovat při vložení**|Pokud je vybraná tato možnost, přeformátuje editoru kódu při vložení do editoru kódu. Editor používá aktuálně definovaných pravidel formátování. Pokud tato možnost není vybraná, používá editor původní formátování kódu vložili se změnami.|

## <a name="new-lines"></a>Nové řádky
 Tyto možnosti určují, zda Editor kódu umístí na nový řádek levou složenou závorku funkce a řídicí bloky.

### <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

|Možnost|Popis|
|------------|-----------------|
|**Umístit levou složenou závorku na nový řádek pro funkce**|Pokud je vybraná tato možnost, Editor kódu přesune levou složenou závorku spojené s funkcí na nový řádek.|
|**Umístit levou složenou závorku na nový řádek pro řídicí bloky**|Pokud je vybraná tato možnost, Editor kódu přesune levou složenou závorku, přidružené řídicí blok (například `if` a `while` řídicí bloky) na nový řádek.|

## <a name="spacing"></a>Mezery
 Tyto možnosti určují, jak budou vkládány mezery v **zdroj** zobrazení.

### <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

|Možnost|Popis|
|------------|-----------------|
|**Vložit mezeru za čárku jako oddělovač**|Pokud je vybraná tato možnost, Editor kódu přidá mezeru za čárkou oddělovače.|
|**Vložit mezeru za středník v příkazech for**|Pokud je vybraná tato možnost, Editor kódu přidá mezeru za každý středník v prvním řádku `for` smyčky.|
|**Vložit mezeru před a za binární operátory**|Pokud je vybraná tato možnost, Editor kódu přidá mezeru před a za binární operátory (například, +, -, & & &#124; &#124;).|
|**Vložit mezeru po klíčovém slovu v příkazech toku řízení**|Pokud je vybraná tato možnost, Editor kódu přidá mezeru za klíčová slova jazyka JavaScript v příkazech toku řízení.|
|**Vložit mezeru za klíčové slovo function pro anonymní funkce**|Pokud je vybraná tato možnost, Editor kódu přidá mezeru za `function` pro anonymní funkce.|
|**Vložit mezeru za levou a před pravou závorku prázdné**|Pokud je vybraná tato možnost, editoru kódu přidá mezeru za levou (otevírací) a před pravou závorku. Pokud jsou k dispozici v rámci závorky prázdné znaky.|

## <a name="see-also"></a>Viz také

- [Obecné, Prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)