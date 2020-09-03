---
title: Sestavování a čištění projektů a řešení
description: Tento článek popisuje, jak sestavit projekt v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.topic: how-to
ms.openlocfilehash: a33b590290880a7e20e7c0ec44c0b12942b1240e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85939098"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Sestavování a čištění projektů a řešení

Podle kroků v tomto článku se dozvíte, jak sestavit, znovu sestavit nebo vyčistit všechny nebo některé projekty v řešení.

> [!NOTE]
> Toto téma se týká Visual Studio pro Mac. V případě sady Visual Studio ve Windows, přečtěte si téma [sestavování a čištění projektů a řešení v aplikaci Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Sestavení, opětovné sestavení nebo vyčištění celého řešení

1. Vyberte uzel řešení v **oblast řešení**:

    ![Výběr uzlu řešení](media/compiling-and-building-image1.png)

2. V řádku nabídek vyberte nabídku **sestavení** a vyberte jednu z následujících možností:

    ![výběr položky nabídky sestavit vše](media/compiling-and-building-image2.png)

    * Zvolením možnosti **sestavit vše** zkompilujte soubory a součásti v rámci projektu, které se od posledního sestavení změnily.

    * Zvolte možnost znovu sestavit vše do "vyčistit" řešení a poté **Sestavte** všechny soubory a součásti projektu.

    * Chcete-li odstranit všechny mezilehlé a výstupní soubory, vyberte možnost **Vyčistit vše** . Pouze v případě, že zbývá pouze soubory projektu a součásti, lze sestavit nové instance zprostředkujících a výstupních souborů.

## <a name="to-build-or-rebuild-a-single-project"></a>Sestavení nebo opětovné sestavení jednoho projektu

1. Vyberte projekt v **oblast řešení**.

2. V řádku nabídek vyberte nabídku **sestavení** .

3. Vyberte buď sestavení [ProjectName], znovu sestavit [ProjectName], nebo vyčištění [ProjectName].

## <a name="to-stop-a-build"></a>Zastavení sestavení

Chcete-li zastavit sestavení, použijte jednu z následujících možností:

* Ve stavové oblasti stiskněte červené čtverce:

    ![Stisknutím červeného čtverce zastavíte sestavování.](media/compiling-and-building-image3.png)

* Použijte položku **zastavit** v nabídce **sestavení** .

* Stiskněte kombinaci kláves **Cmd + Shift + Return**.

## <a name="see-also"></a>Viz také

- [Sestavování a čištění projektů a řešení (Visual Studio ve Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)