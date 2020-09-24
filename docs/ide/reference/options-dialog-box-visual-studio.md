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
ms.openlocfilehash: bad4e0b7db883a7604d674b854a9c3f794715d8d
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2020
ms.locfileid: "91135102"
---
# <a name="options-dialog-box-visual-studio"></a>Dialogové okno Možnosti (Visual Studio)

Dialogové okno **Možnosti** umožňuje nakonfigurovat integrované vývojové prostředí (IDE) podle vašich potřeb. Můžete například vytvořit výchozí umístění pro uložení pro vaše projekty, změnit výchozí vzhled a chování systému Windows a vytvořit zástupce pro běžně používané příkazy. K dispozici jsou také možnosti specifické pro váš vývojový jazyk a platformu. **Možnosti** přístupu můžete získat z nabídky **nástroje** .

## <a name="layout-of-the-options-dialog-box"></a>Rozložení dialogového okna Možnosti

Dialogové okno **Možnosti** je rozdělené na dvě části: navigační podokno vlevo a oblast zobrazení na pravé straně. Strom ovládacího prvku v navigačním podokně obsahuje uzly složek, jako je prostředí, textový editor, projekty a řešení a Správa zdrojového kódu. Rozbalte uzel všechny složky a seznamte se se stránkami možností, které obsahuje. Když vyberete uzel pro konkrétní stránku, zobrazí se jeho možnosti v oblasti zobrazení.

Možnosti pro funkci IDE se v navigačním podokně nezobrazí, dokud se funkce nenačte do paměti. Proto se stejné možnosti nemusí zobrazit při zahájení nové relace, která se zobrazila jako poslední. Při vytváření projektu nebo spuštění příkazu, který používá konkrétní aplikaci, jsou do dialogového okna Možnosti přidány uzly pro příslušné možnosti. Tyto přidané možnosti budou zůstat dostupné, pokud funkce IDE zůstane v paměti.

> [!NOTE]
> Některé kolekce nastavení rozsahují počet stránek, které se zobrazí v navigačním podokně dialogového okna Možnosti. Kliknutím na tlačítko **Zobrazit všechna nastavení**můžete zobrazit všechny možné stránky.

## <a name="how-options-are-applied"></a>Způsob použití možností

Kliknutím na OK v dialogovém okně **Možnosti** uložíte všechna nastavení na všech stránkách. Kliknutím na zrušit na každé stránce se zruší všechny žádosti o změnu, včetně těch, které se právě udělaly na jiných stránkách **možností** . Některé změny nastavení možností, jako jsou provedené v [písmech a barvách, prostředí, dialogové okno Možnosti](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), se projeví až po zavření a opětovném spuštění sady Visual Studio.

## <a name="see-also"></a>Viz také

- [Vlastní nastavení editoru](../how-to-change-text-case-in-the-editor.md)
