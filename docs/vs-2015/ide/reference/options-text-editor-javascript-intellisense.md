---
title: Možnosti, textový editor, JavaScript, IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b0d9dec8ec9b3eb8860bb8b3a4ed8f7347aa54d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662235"
---
# <a name="options-text-editor-javascript-intellisense"></a>Možnosti, textový editor, JavaScript, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stránka **IntelliSense** v dialogovém okně **Možnosti** slouží k úpravě nastavení, která mají vliv na chování technologie IntelliSense pro JavaScript. Stránku **IntelliSense** můžete otevřít výběrem možnosti **nástroje**, **Možnosti** na řádku nabídek a následným rozbalením **textového editoru**, **JavaScriptu**, **IntelliSense.**

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 Stránka **IntelliSense** obsahuje následující části:

## <a name="validation"></a>Ověřování
 Pomocí těchto možností můžete nastavit předvolby toho, jak editor kódu JavaScript validuje syntaxi v dokumentu.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Zobrazit syntaktické chyby** Pokud toto políčko není zaškrtnuté, Editor kódu JavaScriptu nezobrazuje chyby syntaxe. To je užitečné, pokud pracujete s kódem, který jste nenapsali a nehodláte opravovat chyby syntaxe.

 Pokud je toto políčko zaškrtnuté, máte možnost zaškrtnout políčko **Zobrazit chyby jako upozornění** .

 **Zobrazit chyby jako upozornění** Pokud je toto políčko zaškrtnuté, zobrazí se chyby JavaScriptu jako upozornění namísto chyb v seznamu chyb.

 **Stáhnout vzdálené odkazy (např. http://) pro soubory v projektu různé soubory** Pokud je toto políčko zaškrtnuto a pokud máte soubor JavaScriptu otevřený mimo kontext projektu, Visual Studio stáhne vzdálené soubory JavaScriptu, na které se odkazuje v souboru za účelem poskytnutí informací technologie IntelliSense. Při výběru této možnosti se soubory stáhnou, pokud je vložíte jako referenci do souboru s kódem JavaScript.

> [!NOTE]
> Pro webové projekty jsou ve výchozím nastavení vzdálené soubory, na které váš projekt odkazuje, staženy automaticky.

## <a name="statement-completion"></a>Doplňování výrazů
 Tyto možnosti slouží ke změně chování při doplňování výrazů technologie IntelliSense.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Pro potvrzení změn použít pouze tabulátor nebo ENTER** Je-li toto políčko zaškrtnuto, Editor kódu jazyka JavaScript připojí příkazy s položkami vybranými v seznamu pro doplňování až po výběru karty nebo klávesy ENTER. Pokud není zaškrtnuto, mohou se příkazy doplňovat vybranými položkami také při použití jiných znaků, jako je tečka, čárka, dvojtečka, levá závorka a levá složená závorka ({).

## <a name="references"></a>Odkazy
 Pomocí těchto možností lze určit typy souborů .js technologie IntelliSense, které jsou v oboru pro různé typy projektů jazyka JavaScript. Reference IntelliSense se zpravidla používají k zajištění podpory IntelliSense pro globální objekty. Tato stránka navíc umožňuje nastavit pořadí načítání skriptů, které musejí být načteny při spuštění, a přidat soubory s rozšířením IntelliSense.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Referenční skupiny** Tato možnost určuje typ referenční skupiny. Jsou podporovány tři referenční skupiny:

 Pomocí předdefinovaných referenčních skupin můžete určit, že konkrétní soubory .js technologie IntelliSense jsou v oboru pro různé projekty jazyka JavaScript. K dispozici jsou čtyři referenční skupiny:

- Implicitní (Windows *Version*) pro [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikace používající JavaScript Soubory zahrnuté v této skupině jsou v oboru pro každý soubor. js otevřený v editoru kódu pro [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikace využívající JavaScript.

- Implicitní (web) pro projekty HTML5. Soubory zahrnuté v této skupině jsou v oboru pro každý soubor .js otevřený v editoru kódu pro tyto typy projektů.

- Referenční skupiny vyhrazeného pracovníka, pro HTML5 Web Workers. Soubory zahrnuté v této skupině jsou v oboru pro každý soubor .js, který má explicitní odkaz na referenční skupinu vyhrazeného pracovníka.

- Obecné, pro ostatní typy projektů jazyka JavaScript.

  **Zahrnuté soubory** Tato možnost určuje pořadí, ve kterém jsou soubory načteny do kontextu jazykové služby. Pořadí můžete nakonfigurovat pomocí tlačítek **Odebrat**, **Přesunout nahoru**a **Přesunout dolů** . Aby technologie IntelliSense správně fungovala, musí se po určení souboru načíst soubor, který je na něm závislý.

> [!CAUTION]
> Pokud je objekt definován nepodmíněně ve dvou nebo více implicitních odkazech, použije se k definování tohoto objektu poslední odkaz v tomto seznamu.

 **Přidat odkaz na skupinu** Tato možnost poskytuje způsob, jak přidat další soubory IntelliSense. js procházením příslušných souborů.

## <a name="see-also"></a>Viz také
 [JavaScript IntelliSense](../../ide/javascript-intellisense.md)
