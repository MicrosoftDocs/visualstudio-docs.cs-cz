---
title: Dialogové okno Možnosti
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c864a10af9ad15d47e2342bb148af464b8f2a0d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591499"
---
# <a name="options-dialog-box-visual-studio"></a>Dialogové okno Možnosti (Visual Studio)

Dialogové okno **Možnosti** umožňuje nakonfigurovat integrované vývojové prostředí (IDE) podle vašich potřeb. Můžete například vytvořit výchozí umístění pro uložení pro projekty, změnit výchozí vzhled a chování oken a vytvořit zástupce pro běžně používané příkazy. K dispozici jsou také možnosti specifické pro váš vývojový jazyk a platformu. K **možnostem** můžete přistupovat z nabídky **Nástroje.**

## <a name="layout-of-the-options-dialog-box"></a>Rozložení dialogového okna Možnosti

Dialogové okno **Možnosti** je rozděleno na dvě části: navigační podokno vlevo a oblast zobrazení vpravo. Ovládací prvek stromu v navigačním podokně obsahuje uzly složek, například Prostředí, Textový editor, Projekty a řešení a Řízení zdrojového kódu. Rozbalte libovolný uzel složky a seznam stránek možností, které obsahuje. Když vyberete uzel pro určitou stránku, jeho volby se zobrazí v oblasti zobrazení.

Možnosti funkce IDE se v navigačním podokně nezobrazí, dokud se tato funkce nenačte do paměti. Proto stejné možnosti nemusí být zobrazeny při zahájení nové relace, které byly zobrazeny jako ukončení poslední. Když vytvoříte projekt nebo spustíte příkaz, který používá určitou aplikaci, budou do dialogového okna Možnosti přidány uzly pro příslušné možnosti. Tyto přidané možnosti pak zůstanou k dispozici tak dlouho, dokud funkce IDE zůstane v paměti.

> [!NOTE]
> Některé kolekce nastavení obor počet stránek, které se zobrazí v navigačním podokně dialogového okna Možnosti. Všechny možné stránky můžete zobrazit výběrem možnosti **Zobrazit všechna nastavení**.

## <a name="how-options-are-applied"></a>Způsob použití možností

Klepnutím na TLAČÍTKO OK v dialogovém okně **Možnosti** se uloží všechna nastavení na všechny stránky. Kliknutím na tlačítko Storno na libovolné stránce zrušíte všechny žádosti o změnu, včetně všech, které byly provedeny na jiných stránkách **Možností.** Některé změny nastavení možností, například provedené v [dialogovém okně Písma a barvy, Prostředí, Možnosti](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), se projeví až po zavření a opětovném otevření sady Visual Studio.

### <a name="show-all-settings"></a>Zobrazit všechna nastavení

Výběr nebo zrušení **výběru: Zobrazit všechna nastavení** platí všechny změny, které jste provedli v dialogovém okně **Volby,** i když jste ještě neklepali na **OK**.

## <a name="see-also"></a>Viz také

- [Vlastní nastavení editoru](../how-to-change-text-case-in-the-editor.md)
