---
title: Sestavování a čištění projektů a řešení
description: Tento článek popisuje, jak vytvořit projekt v Sadě Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 924bdb08154ecb3caad04cabf7e860bed9204e98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128460"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Stavební a úklidové projekty a řešení

Postupujte podle kroků v tomto článku se dozvíte, jak vytvořit, znovu sestavit nebo vyčistit všechny nebo některé projekty v řešení.

> [!NOTE]
> Toto téma se týká Visual Studia pro Mac. Visual Studio ve Windows najdete v [tématu vytváření a čištění projektů a řešení v sadě Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Vytvoření, opětovné sestavení nebo čištění celého řešení

1. Vyberte uzel Řešení v **panelu řešení**:

    ![Výběr uzlu řešení](media/compiling-and-building-image1.png)

2. Vyberte nabídku **Sestavit** na řádku nabídek a zvolte jednu z následujících voleb:

    ![výběr položky nabídky Sestavení vše](media/compiling-and-building-image2.png)

    * Zvolte **Sestavit vše** pro kompilaci souborů a součástí v rámci projektu, které se změnily od posledního sestavení.

    * Zvolte **Znovu sestavit vše** "vyčistit" řešení a pak vytvoří všechny soubory projektu a součásti.

    * Zvolte **Vyčistit vše,** chcete-li odstranit všechny zprostředkující a výstupní soubory. S pouze projekt a dílčí soubory vlevo, nové instance zprostředkující a výstupní soubory pak mohou být vytvořeny.

## <a name="to-build-or-rebuild-a-single-project"></a>Vytvoření nebo opětovné sestavení jednoho projektu

1. Vyberte projekt v panelu **řešení**.

2. Z řádku nabídek vyberte nabídku **Sestavení.**

3. Zvolte buď Build[Název_projektu], Znovu sestavit[Název_projektu] nebo Vyčistit[Název_projektu].

## <a name="to-stop-a-build"></a>Zastavení sestavení

Chcete-li zastavit sestavení, použijte jednu z následujících možností:

* Stiskněte červený čtverec ve stavové oblasti:

    ![Stisknutím červeného čtverce zastavíte sestavení](media/compiling-and-building-image3.png)

* Použijte položku **Zastavit** v nabídce **Sestavení.**

* Stiskněte **tlačítko Cmd+Shift+Return**.

## <a name="see-also"></a>Viz také

- [Vytváření a čištění projektů a řešení (Visual Studio ve Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)