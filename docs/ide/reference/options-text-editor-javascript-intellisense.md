---
title: Možnosti, textový editor, JavaScript, IntelliSense
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.IntelliSense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3d030e028332bd57afe66eee31c888713721212
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68605977"
---
# <a name="options-dialog-box-text-editor--javascript--intellisense"></a>Dialogové okno Možnosti: textový editor \> JavaScript \> IntelliSense

Stránka **IntelliSense** v dialogovém okně **Možnosti** slouží k úpravě nastavení, která mají vliv na chování technologie IntelliSense pro JavaScript. Stránku **IntelliSense** můžete otevřít výběrem **Tools**  >  **možností** nástroje na panelu nabídek a následným rozbalením **textového editoru**  >  **JavaScript/TypeScript**  >  **IntelliSense.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Stránka **IntelliSense** obsahuje následující části:

## <a name="statement-completion"></a>Doplňování výrazů

Tyto možnosti slouží ke změně chování při doplňování výrazů technologie IntelliSense.

### <a name="uielement-list"></a>UIElement – seznam

**Pro potvrzení změn použít pouze tabulátor nebo ENTER**

Když zaškrtnete toto políčko, Editor kódu JavaScript připojí příkazy s položkami vybranými v seznamu pro doplňování až po výběru **karty** nebo klávesy **ENTER** . Když zrušíte zaškrtnutí tohoto políčka, ostatní znaky – například tečka, čárka, dvojtečka, Otevírací závorka a levá složená závorka ({) – mohou také připojit příkazy s vybranými položkami.

## <a name="references"></a>Odkazy

Pomocí těchto možností lze určit typy souborů .js technologie IntelliSense, které jsou v oboru pro různé typy projektů jazyka JavaScript. Reference IntelliSense se zpravidla používají k zajištění podpory IntelliSense pro globální objekty. Tato stránka navíc umožňuje nastavit pořadí načítání skriptů, které musejí být načteny při spuštění, a přidat soubory s rozšířením IntelliSense.

### <a name="uielement-list"></a>UIElement – seznam

**Referenční skupiny**

Tato možnost určuje typ referenční skupiny. Jsou podporovány tři referenční skupiny:

Pomocí předdefinovaných referenčních skupin můžete určit, že konkrétní soubory .js technologie IntelliSense jsou v oboru pro různé projekty jazyka JavaScript. K dispozici jsou čtyři referenční skupiny:

- Implicitní (Windows *Version*) pro [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikace používající JavaScript Soubory zahrnuté v této skupině jsou v oboru pro každý soubor. js otevřený v editoru kódu pro [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikace využívající JavaScript.

- Implicitní (web) pro projekty HTML5. Soubory zahrnuté v této skupině jsou v oboru pro každý soubor .js otevřený v editoru kódu pro tyto typy projektů.

- Referenční skupiny vyhrazených pracovních procesů pro webové pracovní procesy HTML5 Soubory zahrnuté v této skupině jsou v oboru pro každý soubor .js, který má explicitní odkaz na referenční skupinu vyhrazeného pracovníka.

- Obecné, pro ostatní typy projektů jazyka JavaScript.

**Zahrnuté soubory**

Tato možnost určuje pořadí, v jakém se soubory načítají do kontextu jazykové služby. Pořadí můžete nakonfigurovat pomocí tlačítek **Odebrat**, **Přesunout nahoru**a **Přesunout dolů** . Aby technologie IntelliSense správně fungovala, musí se po určení souboru načíst soubor, který je na něm závislý.

> [!CAUTION]
> Pokud je objekt definován nepodmíněně ve dvou nebo více implicitních odkazech, použije se k definování tohoto objektu poslední odkaz v tomto seznamu.

**Přidat odkaz na skupinu**

Tato možnost poskytuje způsob, jak přidat další soubory .js technologie IntelliSense vyhledáním příslušných souborů.

**Stáhnout vzdálené odkazy (např. http://) pro soubory v projektu různé soubory**

Pokud je toto políčko zaškrtnuto a pokud máte soubor JavaScriptu otevřený mimo kontext projektu, aplikace Visual Studio stáhne vzdálené soubory JavaScriptu, na které se odkazuje v souboru za účelem poskytnutí informací technologie IntelliSense. Pokud je vybrána tato možnost, soubory budou staženy, když je zahrnete jako odkaz do souboru JavaScriptu.

> [!NOTE]
> Pro webové projekty se vzdálené soubory, na které se odkazuje v projektu, stahují ve výchozím nastavení.

## <a name="see-also"></a>Viz také

- [JavaScript IntelliSense](../../ide/javascript-intellisense.md)