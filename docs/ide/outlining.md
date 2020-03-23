---
title: Sbalení a rozšíření oblastí kódu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 781c9a6bc30f7d3a29bcb89e743600e6b29e6445
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585753"
---
# <a name="outlining"></a>Sbalování

Můžete skrýt některé kód ze zobrazení sbalením oblasti kódu tak, aby**+** se zobrazí pod znaménkem plus ( ). Sbalenou oblast rozbalíte kliknutím na znaménko plus. Pokud jste uživatel klávesnice, můžete zvolit **Ctrl**+**M**+**M** sbalit a rozbalit. Oblast osnovy můžete také sbalit poklepáním na libovolný řádek v oblasti na okraji osnovy, který se zobrazí vlevo od kódu. Obsah sbalené oblasti můžete zobrazit jako popis, když nastoli na sbalenou oblast.

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Zdrojový editor (Visual Studio pro Mac).](/visualstudio/mac/source-editor)

Oblasti v okraji osnovy se také zvýrazní, když na okraj najedete myší. Výchozí barva zvýraznění se může v některých barevných konfiguracích jevit jako spíše slabá. Můžete jej změnit v **možnosti nástroje** > **prostředí** > **Environment** > **písma a barvy** > **sbalitelné oblasti**.

Při práci v kódu s přehledem můžete rozbalit oddíly, na kterých chcete pracovat, sbalit je po dokončení a pak přesunout do jiných oddílů. Pokud si nepřejete, aby se zobrazovalo osnovy, můžete pomocí příkazu **Zastavit osnovu** odebrat informace osnovy, aniž byste narušili základní kód.

Příkazy **Vrátit** a **znovu v** nabídce **Úpravy** ovlivní tyto akce. Operace **Kopírování**, **Vyjmout**, **Vložit**a přetažení zachovávají informace o osnovách, ale ne o stavu sbalitelné oblasti. Například při kopírování oblasti, která je sbalená, operace **Vložit** vloží zkopírovaný text jako rozbalené oblasti.

> [!CAUTION]
> Změníte-li nastíněnou oblast, může dojít ke ztrátě osnovy. Například odstranění nebo najít a nahradit operace může vymazat konec oblasti.

Následující příkazy naleznete v podnabídce **Upravit** > **osnovy.**

|||
|-|-|
|Skrýt výběr|(**Ctrl**+**M**, **Ctrl**+**H**) - Sbalí vybraný blok kódu, který `if` by normálně nebyl k dispozici pro osnovu, například blok. Chcete-li odebrat vlastní oblast, použijte **použít možnost Zastavit skrytí aktuálního** stavu (nebo **Ctrl**+**M**, **Ctrl**+**U**). Není k dispozici v jazyce Visual Basic.|
|Přepnout rozšíření osnovy|- Obrátí aktuální skrytý nebo rozšířený stav nejvnitřnějšího oddílu osnovy, když kurzor leží v vnořené sbalené části.|
|Přepnout všechny osnovy|(**Ctrl**+**M**, **Ctrl**+**L**) - Nastaví všechny oblasti do stejného sbaleného nebo rozbaleného stavu. Pokud jsou některé oblasti rozbaleny a některé sbaleny, pak se rozbalí sbalené oblasti.|
|Zastavit osnovu|**(Ctrl**+**M**, **Ctrl**+**P**) - Odstraní všechny informace o výsuších pro celý dokument.|
|Zastavit skrytí aktuálního stavu|(**Ctrl**+**M**, **Ctrl**+**U**) - Odebere informace o osnově pro aktuálně vybranou uživatelem definovanou oblast. Není k dispozici v jazyce Visual Basic.|
|Sbalit na definice|(**Ctrl**+**M**, **Ctrl**+**O**) - Sbalí členy všech typů.|
|Sbalit\<blok: logická hranice>|(C++) Sbalí oblast funkce obsahující kurzor. Pokud například kurzor leží uvnitř smyčky, smyčka je skrytá.|
|Sbalit \<vše v: logické struktury>|(C++) Sbalí všechny struktury uvnitř funkce.|

Pomocí sady Visual Studio SDK můžete také definovat textové oblasti, které chcete rozbalit nebo sbalit. Viz [návod: Osnova](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Zdrojový editor (Visual Studio pro Mac)](/visualstudio/mac/source-editor)
