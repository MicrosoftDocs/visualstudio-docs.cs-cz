---
title: Možnosti, textový editor, JavaScript, formátování
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 957dbd557a15c4c1df6028672f204a06936767c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68605997"
---
# <a name="options-dialog-box-text-editor--javascript--formatting"></a>Dialogové okno Možnosti: \> Formátování JavaScriptu textového editoru \>

Pomocí stránky **Formátování** v dialogovém okně **Možnosti** nastavte volby pro formátování kódu v Editoru kódu. Chcete-li získat přístup k této stránce, zvolte na řádku nabídek**možnosti** **nástrojů** > a potom **rozbalte** > **formátování JavaScript/TypeScript** > **textového editoru**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Automatické formátování

Tyto možnosti určují, kdy dojde k formátování ve **zdrojovém** zobrazení.

### <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

|Možnost|Popis|
|------------|-----------------|
|**Formát dokončený řádek na Enter**|Když je tato volba vybraná, Editor kódu automaticky zformátuje řádek, když zvolíte klávesu Enter.|
|**Formát dokončeného příkazu dne ;**|Je-li vybrána tato možnost, Editor kódu automaticky zformátuje řádek, když zvolíte středník.|
|**Formát otevřený blok na {**|Je-li vybrána tato možnost, Editor kódu automaticky zformátuje řádek, když zvolíte otevírací složenou složenku.|
|**Formát dokončen blok na }**|Je-li vybrána tato možnost, Editor kódu automaticky zformátuje řádek, když zvolíte uzavírací složenou složenou klávesu.|
|**Formát při vložení**|Když je vybrána tato možnost, Editor kódu přeformátuje kód, když jej vložíte do editoru. Editor používá aktuálně definovaná pravidla formátování. Pokud tato volba není vybrána, editor použije původní formátování vloženého kódu.|

## <a name="new-lines"></a>Nové řádky

Tyto možnosti určují, zda Editor kódu umístí otevřenou složenou složenku pro funkce a řídicí bloky na nový řádek.

### <a name="uielement-list"></a>Seznam Prvků UI

|Možnost|Popis|
|------------|-----------------|
|**Umístit otevřenou ortézu na nový řádek pro funkce**|Je-li vybrána tato možnost, Editor kódu přesune otevřenou složenou závorku přidruženou k funkci na nový řádek.|
|**Umístit otevřenou složenou závorku na novou čáru pro řídicí bloky**|Je-li vybrána tato možnost, Editor kódu přesune otevřenou složenou závorku přidruženou k řídicímu bloku (například `if` řídicím `while` blokům) na nový řádek.|

## <a name="spacing"></a>Mezery

Tyto možnosti určují způsob vkládání mezer do **zdrojového** zobrazení.

### <a name="uielement-list"></a>Seznam Prvků UI

|Možnost|Popis|
|------------|-----------------|
|**Vložení mezery za oddělovač čárky**|Je-li vybrána tato možnost, editor kódu přidá mezeru za oddělovače čárek.|
|**Vložit mezeru za středník do příkazů 'for'**|Je-li vybrána tato možnost, Editor kódu přidá mezeru za `for` každý středník v prvním řádku smyčky.|
|**Vložení mezery před a za binární operátory**|Pokud je vybrána tato možnost, Editor kódu přidá mezeru před a za binární operátory (například +, -, &&, &#124;&#124;).|
|**Vložení mezery za klíčová slova do příkazů toku řízení**|Je-li vybrána tato volba, Editor kódu přidá mezeru za klíčová slova JavaScriptu do příkazů toku řízení.|
|**Vložit mezeru za funkci klíčové slovo pro anonymní funkce**|Je-li vybrána tato možnost, editor `function` kódu přidá mezeru za klíčové slovo pro anonymní funkce.|
|**Vložení mezery po otevření a před zavřením neprázdné závorky**|Je-li vybrána tato možnost, editor kódu přidá mezeru za počáteční závorku a před uzavírací závorku, pokud jsou v závorcích neprázdné znaky.|

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)