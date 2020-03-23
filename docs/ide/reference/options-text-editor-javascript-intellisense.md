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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68605977"
---
# <a name="options-dialog-box-text-editor--javascript--intellisense"></a>Dialogové okno Možnosti: Text Editor \> JavaScript \> IntelliSense

Pomocí stránky **IntelliSense** v dialogovém okně **Možnosti** můžete upravit nastavení, která ovlivňují chování technologie IntelliSense pro JavaScript. Na stránku **IntelliSense** se dostanete tak, že na řádku nabídek zvolíte**Možnosti** **nástrojů** > a pak rozbalíte **textový editor** > **JavaScript/TypeScript** > **IntelliSense.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Stránka **IntelliSense** obsahuje následující části:

## <a name="statement-completion"></a>Doplňování výrazů

Tyto možnosti slouží ke změně chování při doplňování výrazů technologie IntelliSense.

### <a name="uielement-list"></a>Seznam Prvků UI

**K potvrzení používejte pouze kartu nebo enter.**

Když toto políčko zaškrtnete, editor kódu Jazyka JavaScript připojí příkazy s položkami vybranými v seznamu dokončení až po výběru **klávesy Tab** nebo **Enter.** Když zrušíte zaškrtnutí tohoto políčka, mohou k vybraným položkám připojit příkazy také jiné znaky, například tečka, čárka, dvojtečka, otevřená závorka a otevřená závorka ({).

## <a name="references"></a>Odkazy

Pomocí těchto možností lze určit typy souborů .js technologie IntelliSense, které jsou v oboru pro různé typy projektů jazyka JavaScript. Reference IntelliSense se zpravidla používají k zajištění podpory IntelliSense pro globální objekty. Tato stránka navíc umožňuje nastavit pořadí načítání skriptů, které musejí být načteny při spuštění, a přidat soubory s rozšířením IntelliSense.

### <a name="uielement-list"></a>Seznam Prvků UI

**Referenční skupiny**

Tato možnost určuje typ referenční skupiny. Jsou podporovány tři referenční skupiny:

Pomocí předdefinovaných referenčních skupin můžete určit, že konkrétní soubory .js technologie IntelliSense jsou v oboru pro různé projekty jazyka JavaScript. K dispozici jsou čtyři referenční skupiny:

- Implicitní *(verze* [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] windows) pro aplikace používající JavaScript. Soubory obsažené v této skupině jsou v oboru pro každý [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] soubor JS otevřený v Editoru kódu pro aplikace používající JavaScript.

- Implicitní (web) pro projekty HTML5. Soubory zahrnuté v této skupině jsou v oboru pro každý soubor .js otevřený v editoru kódu pro tyto typy projektů.

- Vyhrazené pracovní referenční skupiny pro webové pracovníky HTML5. Soubory zahrnuté v této skupině jsou v oboru pro každý soubor .js, který má explicitní odkaz na referenční skupinu vyhrazeného pracovníka.

- Obecné, pro ostatní typy projektů jazyka JavaScript.

**Zahrnuté soubory**

Tato možnost určuje pořadí, v jakém se soubory načítají do kontextu jazykové služby. Pořadí můžete nakonfigurovat pomocí tlačítek **Odebrat**, **Přesunout nahoru**a **Přesunout dolů.** Aby technologie IntelliSense správně fungovala, musí se po určení souboru načíst soubor, který je na něm závislý.

> [!CAUTION]
> Pokud je objekt definován nepodmíněně ve dvou nebo více implicitních odkazech, použije se k definování tohoto objektu poslední odkaz v tomto seznamu.

**Přidání odkazu na skupinu**

Tato možnost poskytuje způsob, jak přidat další soubory .js technologie IntelliSense vyhledáním příslušných souborů.

**Stažení vzdálených odkazů (např. http://) pro soubory v projektu různé soubory**

Pokud je toto políčko zaškrtnuto a máte otevřený soubor JavaScript mimo kontext projektu, aplikace Visual Studio stáhne vzdálené soubory JavaScriptu, na které se v souboru odkazuje, za účelem poskytnutí informací o programu IntelliSense. Pokud je tato volba vybraná, soubory se stáhnou, když je zahrnete jako referenci do souboru JavaScript.

> [!NOTE]
> U webových projektů se ve výchozím nastavení stahují vzdálené soubory odkazované v projektu.

## <a name="see-also"></a>Viz také

- [JavaScript IntelliSense](../../ide/javascript-intellisense.md)