---
title: Refaktoring kódu
description: Rafinace kódu pomocí Visual Studio pro Mac a rychlých akcí.
author: jmatthiesen
ms.author: jomatthi
ms.date: 07/03/2020
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 3892117e5c84a71f258d4e019105fca0a8cf9c5b
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189235"
---
# <a name="refactoring"></a>Refaktoring

Refaktoring kódu je způsob, jak změnit uspořádání, restrukturování a objasnění stávajícího kódu a přitom zajistit, že se celkové chování kódu nezmění.

Refaktoring vytváří základ kódu umožňovat, takže je bezpečnější, čitelný a udržovatelný pro vás nebo jakýkoli jiný vývojář nebo uživatel, který může odkazovat na kód.

Visual Studio pro Mac integrace s Roslyn, open source platformou .NET od Microsoftu, umožňuje další operace refaktoringu.

## <a name="renaming"></a>Měníte

Příkaz refaktoringu *přejmenování* lze použít pro libovolný identifikátor kódu (například název třídy, název vlastnosti atd.), chcete-li najít všechny výskyty daného identifikátoru a změnit je. Chcete-li symbol přejmenovat, klikněte na něj pravým tlačítkem myši a vyberte příkaz **Přejmenovat...** nebo použijte klávesovou zkratku **cmd (⌘) + R** :

![Přejmenovat položku nabídky](media/refactoring-renaming1.png)

Tím se zvýrazní symbol a všechny odkazy na něj. Když začnete psát nový název, automaticky se změní všechny odkazy v kódu a můžete potvrdit změny stisknutím klávesy **ENTER**:

![Přejmenování a identifikátor](media/refactoring-renaming2.png)

## <a name="quick-actions-and-refactorings"></a>Rychlé akce a refaktoringy

Rychlé akce a refaktoringy umožňují snadno Refaktorovat, generovat nebo jinak upravovat kód jedinou akcí.

Rychlé akce lze použít k těmto akcím:

* Použití opravy kódu pro porušení pravidla analyzátoru kódu
* Potlačit porušení pravidla analyzátoru kódu
* Použít refaktoring (například vložit dočasnou proměnnou)
* Generovat kód (například zavést místní proměnnou)

Rychlé akce lze použít pomocí ikony žárovky žárovky ![ ](media/quick-actions-light-bulb-icon.png) nebo ![ ikon ikon Screwdriver Screwdriver ](media/quick-actions-screwdriver-icon.png) nebo stisknutím **Možnosti (⌥)** + **Zadejte** , když je kurzor na řádku kódu, pro který je akce k dispozici. ![ ](media/quick-actions-error-light-bulb-icon.png) Pokud je červená vlnovka upozorňující na chybu a pro tuto chybu je k dispozici, zobrazí se ikona světlejší žárovky chyba žárovky chyby.

Pro libovolný jazyk mohou třetí strany poskytovat vlastní diagnostiku a návrhy, například jako součást sady SDK a žárovky Visual Studio na základě těchto pravidel.

### <a name="quick-action-icons"></a>Ikony rychlých akcí
Ikona, která se zobrazí, když je rychlá akce k dispozici, poskytne označení typu opravit nebo Refaktoring, který je k dispozici. *screwdriver* ![ Ikona ikony Screwdriver Screwdriver ](media/quick-actions-screwdriver-icon.png) značí, že jsou k dispozici akce pro změnu kódu, ale neměli byste je nutně používat. *yellow light bulb* ![ Ikona ikony žárovky žluté žárovky ](media/quick-actions-light-bulb-icon.png) indikuje, že jsou k dispozici akce, které *byste měli* udělat pro zlepšení kódu. Ikona ikony žárovky chyby světlejší *žárovky* ![ ](media/quick-actions-error-light-bulb-icon.png) indikuje, že je k dispozici akce, která opravuje chybu ve vašem kódu.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>Chcete-li zobrazit žárovku nebo Screwdriver

- Pokud je oprava k dispozici, žárovky se po najetí myši na místo chyby zobrazí.

   ![Žárovka při najetí myší](media/refactoring-lightbulb-hover.png)

- Žárovky a screwdrivers se zobrazí v levém okraji editoru, když přesunete blikající kurzor na řádek kódu, pro který je k dispozici rychlá akce nebo refaktoring.

- Stisknutím **Možnosti (⌥)** + **Zadejte** libovolné místo na řádku, abyste viděli seznam dostupných rychlých akcí a refaktoringů.

![Zobrazit položky kontextu](media/refactoring-context-action.png)

Najetí myší na kteroukoli z kontextových akcí vám poskytne náhled toho, co se přidá nebo odebere z vašeho kódu.

![Možnost zadat kontextové položky](media/refactoring-image2a.png)

Chcete-li povolit tyto možnosti, je nutné vybrat možnost *Povolit analýzu zdroje otevřených souborů* v části možnosti **Visual Studio pro Mac > předvolby > textový editor > analýza zdroje**:

![Povolení analýzy zdrojů](media/refactoring-options.png)

K dispozici jsou více než 100 možných akcí, které je možné navrhnout, které jsou povolené nebo zakázané, a to tak, že přejdete na **Visual Studio pro Mac > předvolby > zdrojové analýzy > akce v C# > kódu** a zaškrtnete nebo odškrtnete políčko vedle této akce:

![Akce analýzy zdroje v C#](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Běžné rychlé akce

Další informace o běžných rychlých akcích najdete v článku [běžné rychlé akce](/visualstudio/ide/common-quick-actions) .

## <a name="source-analysis"></a>Zdrojová analýza

Zdrojová analýza analyzuje kód průběžně díky podtržením potenciálních chyb a porušení stylu a poskytování automatických oprav jako akcí kontextu.

Všechny výsledky analýzy zdrojů můžete kdykoli zobrazit v libovolném souboru zobrazením posuvníku na pravé straně textového editoru:

![Postranení zdrojové analýzy](media/refactoring-image4a.png)

Pokud kliknete na kolečko v horní části, můžete iterovat každý návrh s nejvyššími problémy závažnosti, které se zobrazí jako první. Najetí myší na jednotlivý výsledek nebo řádek zobrazí problém, který se dá opravit prostřednictvím kontextových akcí:

![Zdrojová položka analýzy](media/refactoring-image5.png)

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Viz také

- [Rychlé akce (Visual Studio ve Windows)](/visualstudio/ide/quick-actions)
- [Refaktoring kódu (Visual Studio ve Windows)](/visualstudio/ide/refactoring-in-visual-studio)
