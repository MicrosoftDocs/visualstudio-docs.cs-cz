---
title: Dialogové okno Možnosti
description: Přečtěte si o dialogovém okně Možnosti, jeho rozložení a o tom, jak vizuální studia aplikují vybrané možnosti na vaše projekty a řešení.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 79bd2d95a12aa7c42705d106cf71b4061a020431
ms.sourcegitcommit: 113b7df611583307d3965984233a33355d6b0318
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/16/2021
ms.locfileid: "112126538"
---
# <a name="options-dialog-box-visual-studio"></a>Dialogové okno Možnosti (Visual Studio)

Dialogové **okno** Možnosti umožňuje konfigurovat integrované vývojové prostředí (IDE) podle vašich potřeb. Můžete například vytvořit výchozí umístění pro ukládání projektů, změnit výchozí vzhled a chování oken a vytvořit zástupce pro běžně používané příkazy. Existují také možnosti specifické pro váš vývojový jazyk a platformu. K možnostem **můžete přistupovat** z **nabídky** Nástroje.

## <a name="layout-of-the-options-dialog-box"></a>Rozložení dialogového okna Možnosti

Dialogové **okno** Možnosti je rozdělené na dvě části: navigační podokno vlevo a oblast zobrazení na pravé straně. Ovládací prvek stromové struktury v navigačním podokně obsahuje uzly složek, například Prostředí, Textový editor, Projekty a řešení a Source Control. Rozbalte libovolný uzel složky a zobrazí se seznam stránek s možnostmi, které obsahuje. Když vyberete uzel pro konkrétní stránku, zobrazí se jeho možnosti v oblasti zobrazení.

Možnosti funkce integrovaného vývojového prostředí se v navigačním podokně nezobrazí, dokud se tato funkce nenačítá do paměti. Proto se při zahájení nové relace, která se při ukončení poslední relace zobrazuje, nemusí být zobrazeny stejné možnosti. Když vytvoříte projekt nebo spustíte příkaz, který používá konkrétní aplikaci, uzly pro relevantní možnosti se přidávají do dialogového okna Možnosti. Tyto přidané možnosti pak zůstanou dostupné, dokud zůstane funkce integrovaného vývojového prostředí v paměti.

> [!NOTE]
> V některých kolekcích nastavení je vymezen počet stránek, které se zobrazí v navigačním podokně dialogového okna Možnosti.

## <a name="how-options-are-applied"></a>Způsob použití možností

Kliknutím na OK v **dialogovém okně** Možnosti uložíte všechna nastavení na všech stránkách. Kliknutím na Zrušit na jakékoli stránce zrušíte všechny žádosti o změnu, včetně všech právě provedených na jiných **stránkách** Možnosti. Některé změny nastavení možností, například změny písma a [barev, prostředí,](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md)dialogové okno Možnosti, se projeví až po zavření a opětovném otevření Visual Studio.

## <a name="see-also"></a>Viz také

- [Vlastní nastavení editoru](../how-to-change-text-case-in-the-editor.md)
- [Nastavení a předvolby Gitu](../../version-control/git-settings.md)
