---
title: Sestavování a čištění projektů a řešení
description: Tento článek popisuje, jak sestavit projekt v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 924bdb08154ecb3caad04cabf7e860bed9204e98
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128460"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Sestavování a čištění projektů a řešení

Podle kroků v tomto článku se dozvíte, jak sestavit, znovu sestavit nebo vyčistit všechny nebo některé projekty v řešení.

> [!NOTE]
> Toto téma se týká Visual Studio pro Mac. V případě sady Visual Studio ve Windows, přečtěte si téma [sestavování a čištění projektů a řešení v aplikaci Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Pokud chcete vytvořit, znovu sestavit nebo vyčištění celé řešení

1. Vyberte uzel řešení v **oblast řešení**:

    ![Výběr uzlu řešení](media/compiling-and-building-image1.png)

2. V řádku nabídek vyberte nabídku **sestavení** a vyberte jednu z následujících možností:

    ![výběr položky nabídky sestavit vše](media/compiling-and-building-image2.png)

    * Zvolením možnosti **sestavit vše** zkompilujte soubory a součásti v rámci projektu, které se od posledního sestavení změnily.

    * Zvolte možnost znovu sestavit vše do "vyčistit" řešení a poté **Sestavte** všechny soubory a součásti projektu.

    * Chcete-li odstranit všechny mezilehlé a výstupní soubory, vyberte možnost **Vyčistit vše** . Pouze projekt a součást soubory vlevo nových instancí přechodný a výstupních souborů může pak být sestavena.

## <a name="to-build-or-rebuild-a-single-project"></a>Chcete-li sestavit nebo opětovně sestavit jeden projekt

1. Vyberte projekt v **oblast řešení**.

2. V řádku nabídek vyberte nabídku **sestavení** .

3. Vyberte buď sestavení [ProjectName], znovu sestavit [ProjectName], nebo vyčištění [ProjectName].

## <a name="to-stop-a-build"></a>Zastavit sestavení

Chcete-li zastavit sestavení, použijte jednu z následujících možností:

* Ve stavové oblasti stiskněte červené čtverce:

    ![Stisknutím červeného čtverce zastavíte sestavování.](media/compiling-and-building-image3.png)

* Použijte položku **zastavit** v nabídce **sestavení** .

* Stiskněte kombinaci kláves **Cmd + Shift + Return**.

## <a name="see-also"></a>Viz také:

- [Sestavování a čištění projektů a řešení (Visual Studio ve Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)