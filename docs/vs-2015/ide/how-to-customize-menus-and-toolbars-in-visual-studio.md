---
title: 'Postupy: Přizpůsobení nabídek a panelů nástrojů'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3196aac35a05d915f1f4c3b58547e0787e9a1afc
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066701"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Postupy: Přizpůsobení nabídek a panelů nástrojů v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio si můžete přizpůsobit nejen tak, že přidáte nebo odeberete panely nástrojů a nabídky na řádku nabídek, ale také tak, že přidáte nebo odeberete příkazy na jakémkoli daném panelu nástrojů nebo nabídce.

> [!WARNING]
>  Po přizpůsobení panelu nástrojů nebo nabídky, ujistěte se, že jeho zaškrtávací políčko zaškrtnuto v **vlastní** dialogové okno. V opačném případě se vaše změny po ukončení a opětovném spuštění sady Visual Studio nezachovají.

 **V tomto tématu:**

-   [Přidání, odebrání nebo přesunutí nabídky na řádku nabídek](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addmenu)

-   [Přidání, odebrání nebo přesunutí panelu nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addtoolbar)

-   [Přizpůsobení nabídky nebo panelu nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_customize)

-   [Obnovení nabídky nebo panelu nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_reset)

##  <a name="bkmk_addmenu"></a> Přidání, odebrání nebo přesunutí nabídky na řádku nabídek

1.  V panelu nabídky zvolte **nástroje**, **vlastní**.

     **Vlastní** zobrazí se dialogové okno.

2.  Na **příkazy** kartu, ponechte **nabídek** vybraný přepínač, ponechte **nabídek** vybrán v seznamu vedle této možnosti a pak proveďte jednu z následujících sad pomocí následujících kroků:

    -   Chcete-li přidat nabídku, zvolte **přidat novou nabídku** tlačítko, zvolte **změnit výběr** tlačítko a pak zadejte název nabídky, kterou chcete přidat.

         ![Ukazuje, jak přidat nabídku dialogové okno Přizpůsobit](../ide/media/addmenu.png "PřidatNabídku")

    -   Chcete-li nabídku odebrat, zvolte jej v **ovládací prvky** seznamu a klikněte na tlačítko **odstranit** tlačítko.

    -   Přejděte do nabídky v rámci řádku nabídek zvolte z nabídky **ovládací prvky** seznamu a klikněte na tlačítko **přesunout nahoru** nebo **přesunout dolů** tlačítko.

##  <a name="bkmk_addtoolbar"></a> Přidání, odebrání nebo přesunutí panelu nástrojů

1.  V panelu nabídky zvolte **nástroje**, **vlastní**.

     **Vlastní** zobrazí se dialogové okno.

2.  Na **nástrojů** kartu, proveďte jednu z následujících sad kroků:

    -   Chcete-li přidat panel nástrojů, zvolte **nový** tlačítko, zadejte název panelu nástrojů, které chcete přidat a potom klikněte **OK** tlačítko.

         ![Ukazuje, jak přidat panel nástrojů dialogové okno Přizpůsobit](../ide/media/addtoolbar.png "AddToolbar")

    -   Chcete-li vlastní panel nástrojů odebrat, zvolte jej v **panely nástrojů** seznamu a klikněte na tlačítko **odstranit** tlačítko.

        > [!IMPORTANT]
        >  Můžete odstranit panely nástrojů, které vytvoříte, ale ne výchozí panely nástrojů.

    -   Chcete-li přesunout do jiné umístění ukotvení panelu nástrojů, zvolte jej v **panely nástrojů** klikněte na položku **změnit výběr** tlačítko a pak v zobrazeném seznamu zvolte umístění.

         Panel nástrojů můžete také přetáhnout pomocí jeho levého okraje na libovolné místo v hlavní oblasti ukotvení.

        > [!NOTE]
        >  Další informace o možnostech zlepšení použitelnosti a přístupnosti panelů nástrojů naleznete v tématu [postupy: nastavení možností usnadnění přístupu IDE](../ide/reference/how-to-set-ide-accessibility-options.md).

##  <a name="bkmk_customize"></a> Přizpůsobení nabídky nebo panelu nástrojů

1.  V panelu nabídky zvolte **nástroje**, **vlastní**.

     **Vlastní** zobrazí se dialogové okno.

2.  Na **příkazy** kartu, zvolte přepínač pro typ prvku, který chcete upravit.

3.  V seznamu pro daný typ prvku zvolte nabídku nebo panel nástrojů, který chcete upravit, a pak proveďte jednu z následujících skupin kroků:

    -   Chcete-li přidat příkaz, zvolte **přidat příkaz** tlačítko.

         V **přidat příkaz** dialogového okna zvolte položku v **kategorie** , zvolte položku v **příkazy** seznamu a klikněte na tlačítko **OK**tlačítko.

         ![Příkaz dialogové okno Přidat v sadě Visual Studio](../ide/media/addcommand.png "AddCommand")

    -   Chcete-li příkaz odstranit, zvolte jej v **ovládací prvky** seznamu a klikněte na tlačítko **odstranit** tlačítko.

    -   Chcete-li změnit pořadí příkazů, zvolte příkaz v **ovládací prvky** seznamu a klikněte na tlačítko **nahoru** nebo **přesunout dolů** tlačítko.

    -   Chcete-li příkazy rozdělit do skupin, zvolte příkaz v **ovládací prvky** klikněte na položku **změnit výběr** tlačítko a pak zvolte **začít vytvářet skupinu** v zobrazené nabídce.

##  <a name="bkmk_reset"></a> Obnovení nabídky nebo panelu nástrojů

1.  V panelu nabídky zvolte **nástroje**, **vlastní**.

     **Vlastní** zobrazí se dialogové okno.

2.  Na **příkazy** kartu, zvolte přepínač pro typ prvku, který chcete obnovit.

3.  V seznamu pro daný typ prvku zvolte nabídku nebo panel nástrojů, které chcete obnovit.

4.  Zvolte **změnit výběr** tlačítko a pak zvolte **resetování** v zobrazené nabídce.

     Můžete také obnovit všechny nabídky a panely nástrojů výběrem **Obnovit vše** tlačítko.
