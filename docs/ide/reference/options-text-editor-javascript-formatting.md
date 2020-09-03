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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68605997"
---
# <a name="options-dialog-box-text-editor--javascript--formatting"></a>Dialogové okno Možnosti: formátování textového editoru \> JavaScript \>

Stránka **formátování** dialogového okna **Možnosti** slouží k nastavení možností formátování kódu v editoru kódu. Chcete-li získat přístup k této stránce, v řádku **Tools**nabídek zvolte  >  **možnost**nástroje a potom rozbalte formátování **textový editor**  >  **JavaScript/TypeScript**  >  **Formatting**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Automatické formátování

Tyto možnosti určují, kdy se formátování vyskytne v zobrazení **zdroje** .

### <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

|Možnost|Popis|
|------------|-----------------|
|**Formátovat dokončený řádek při zadání**|Pokud je vybrána tato možnost, Editor kódu při volbě klávesy ENTER automaticky zformátuje řádek.|
|**Formátovat dokončený příkaz na;**|Pokud je vybrána tato možnost, Editor kódu při výběru středníku automaticky zformátuje řádek.|
|**Formátovat otevřený blok na {**|Je-li vybrána tato možnost, Editor kódu při volbě počátečního klíče složené závorky automaticky zformátuje řádek.|
|**Formátovat dokončený blok na}**|Je-li vybrána tato možnost, Editor kódu při volbě pravého klíče složené závorky automaticky zformátuje řádek.|
|**Formátovat při vložení**|Pokud je vybrána tato možnost, Editor kódu přeformátuje kód při vložení do editoru. Editor používá aktuálně definovaná pravidla formátování. Pokud tato možnost není vybrána, editor použije původní formátování vloženého kódu.|

## <a name="new-lines"></a>Nové řádky

Tyto možnosti určují, zda editor kódu vloží levou složenou závorku pro funkce a řídicí bloky na nový řádek.

### <a name="uielement-list"></a>UIElement – seznam

|Možnost|Popis|
|------------|-----------------|
|**Pro funkce umístit levou složenou závorku na nový řádek**|Pokud je vybrána tato možnost, Editor kódu přesune levou složenou závorku spojenou s funkcí na nový řádek.|
|**Pro řídicí bloky umístit levou složenou závorku na nový řádek**|Je-li vybrána tato možnost, Editor kódu přesune levou složenou závorku spojenou s řídicím blokem (například `if` a `while` řídicími bloky) na nový řádek.|

## <a name="spacing"></a>Mezery

Tyto možnosti určují, jak jsou mezery vloženy do zobrazení **zdroje** .

### <a name="uielement-list"></a>UIElement – seznam

|Možnost|Popis|
|------------|-----------------|
|**Vložit mezeru za oddělovač čárky**|Pokud je vybrána tato možnost, Editor kódu přidá mezeru za oddělovače čárky.|
|**Vložit mezeru za středník v příkazech for**|Pokud je vybrána tato možnost, Editor kódu přidá mezeru za každou střední hodnotu v prvním řádku `for` smyčky.|
|**Vložit mezeru před a za binární operátory**|Pokud je vybrána tato možnost, Editor kódu přidá mezeru před a za binární operátory (například +,-,  &&  &#124;&#124;).|
|**Vložit mezeru za klíčová slova v příkazech toku řízení**|Pokud je vybrána tato možnost, Editor kódu přidá mezeru za klíčovým slovem jazyka JavaScript v příkazech toku řízení.|
|**Vložit mezeru za klíčové slovo funkce pro anonymní funkce**|Pokud je vybrána tato možnost, Editor kódu přidá mezeru za `function` klíčovým slovem pro anonymní funkce.|
|**Vložit mezeru za levou a před pravou závorku, která není prázdná**|Pokud je vybrána tato možnost, Editor kódu přidá mezeru za levou (otevírací) závorku a před pravou závorku, pokud jsou v závorkách přítomny neprázdné znaky.|

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)