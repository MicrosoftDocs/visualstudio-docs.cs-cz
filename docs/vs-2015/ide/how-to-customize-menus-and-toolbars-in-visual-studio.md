---
title: 'Postupy: Přizpůsobení nabídek a panelů nástrojů'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 500debe6faa62079c6a93185bac409e7a3bf2813
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667995"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Postupy: Přizpůsobení nabídek a panelů nástrojů v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio si můžete přizpůsobit nejen tak, že přidáte nebo odeberete panely nástrojů a nabídky na řádku nabídek, ale také tak, že přidáte nebo odeberete příkazy na jakémkoli daném panelu nástrojů nebo nabídce.

> [!WARNING]
> Po přizpůsobení panelu nástrojů nebo nabídky se ujistěte, že jeho zaškrtávací políčko zůstane zaškrtnuté v dialogovém okně **přizpůsobit** . V opačném případě se vaše změny po ukončení a opětovném spuštění sady Visual Studio nezachovají.

 **V tomto tématu:**

- [Přidání, odebrání nebo přesunutí nabídky na řádku nabídek](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addmenu)

- [Přidání, odebrání nebo přesunutí panelu nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addtoolbar)

- [Přizpůsobení nabídky nebo panelu nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_customize)

- [Obnovení nabídky nebo panelu nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_reset)

## <a name="adding-removing-or-moving-a-menu-on-the-menu-bar"></a><a name="bkmk_addmenu"></a> Přidání, odebrání nebo přesunutí nabídky na řádku nabídek

1. Na řádku nabídek klikněte na **nástroje**, **přizpůsobit**.

     Otevře se dialogové okno **přizpůsobit** .

2. Na kartě **příkazy** ponechte vybraný přepínač **panelu nabídek** , v seznamu vedle této možnosti vyberte **panel nabídek** a pak proveďte jednu z následujících sad kroků:

    - Chcete-li přidat nabídku, klikněte na tlačítko **Přidat novou nabídku** , klikněte na tlačítko **změnit výběr** a potom zadejte název nabídky, kterou chcete přidat.

         ![Dialogové okno přizpůsobit, které ukazuje, jak přidat nabídku](../ide/media/addmenu.png "Akci")

    - Pokud chcete nabídku odebrat, zvolte ji v seznamu **ovládací prvky** a klikněte na tlačítko **Odstranit** .

    - Chcete-li přesunout nabídku v rámci řádku nabídek, zvolte nabídku v seznamu **ovládací prvky** a potom klikněte na tlačítko **Přesunout nahoru** nebo **Přesunout dolů** .

## <a name="adding-removing-or-moving-a-toolbar"></a><a name="bkmk_addtoolbar"></a> Přidání, odebrání nebo přesunutí panelu nástrojů

1. Na řádku nabídek klikněte na **nástroje**, **přizpůsobit**.

     Otevře se dialogové okno **přizpůsobit** .

2. Na kartě **panel nástrojů** proveďte jednu z následujících sad kroků:

    - Chcete-li přidat panel nástrojů, klikněte na tlačítko **Nový** , zadejte název panelu nástrojů, který chcete přidat, a poté klikněte na tlačítko **OK** .

         ![Dialogové okno přizpůsobit, které ukazuje, jak přidat panel nástrojů](../ide/media/addtoolbar.png "AddToolbar")

    - Chcete-li odebrat vlastní panel nástrojů, zvolte jej v seznamu **panely nástrojů** a pak klikněte na tlačítko **Odstranit** .

        > [!IMPORTANT]
        > Můžete odstranit panely nástrojů, které vytvoříte, ale ne výchozí panely nástrojů.

    - Chcete-li přesunout panel nástrojů do jiného umístění ukotvení, zvolte jej v seznamu **panely nástrojů** , klikněte na tlačítko **změnit výběr** a potom zvolte umístění v seznamu, který se zobrazí.

         Panel nástrojů můžete také přetáhnout pomocí jeho levého okraje na libovolné místo v hlavní oblasti ukotvení.

        > [!NOTE]
        > Další informace o tom, jak zlepšit použitelnost a přístupnost panelů nástrojů, naleznete v tématu [How to: set a ACCESSIBILITY IDE Options](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name="customizing-a-menu-or-a-toolbar"></a><a name="bkmk_customize"></a> Přizpůsobení nabídky nebo panelu nástrojů

1. Na řádku nabídek klikněte na **nástroje**, **přizpůsobit**.

     Otevře se dialogové okno **přizpůsobit** .

2. Na kartě **příkazy** klikněte na tlačítko možností pro typ prvku, který chcete přizpůsobit.

3. V seznamu pro daný typ prvku zvolte nabídku nebo panel nástrojů, který chcete upravit, a pak proveďte jednu z následujících skupin kroků:

    - Chcete-li přidat příkaz, klikněte na tlačítko **Přidat příkaz** .

         V dialogovém okně **Přidat příkaz** zvolte položku v seznamu **kategorie** , zvolte položku v seznamu **příkazy** a pak klikněte na tlačítko **OK** .

         ![Dialogové okno Přidat příkaz v aplikaci Visual Studio](../ide/media/addcommand.png "Použijete AddCommand menucommandsetgui")

    - Pokud chcete příkaz Odstranit, vyberte ho v seznamu **ovládací prvky** a pak klikněte na tlačítko **Odstranit** .

    - Chcete-li změnit pořadí příkazů, zvolte příkaz v seznamu **ovládací prvky** a potom klikněte na tlačítko **Přesunout nahoru** nebo **Přesunout dolů** .

    - Chcete-li rozdělit příkazy do skupin, zvolte příkaz v seznamu **ovládací prvky** , klikněte na tlačítko **změnit výběr** a potom v zobrazené nabídce zvolte možnost **zahájit skupinu** .

## <a name="resetting-a-menu-or-a-toolbar"></a><a name="bkmk_reset"></a> Obnovení nabídky nebo panelu nástrojů

1. Na řádku nabídek klikněte na **nástroje**, **přizpůsobit**.

     Otevře se dialogové okno **přizpůsobit** .

2. Na kartě **příkazy** klikněte na tlačítko možností pro typ prvku, který chcete obnovit.

3. V seznamu pro daný typ prvku zvolte nabídku nebo panel nástrojů, které chcete obnovit.

4. Klikněte na tlačítko **změnit výběr** a potom v zobrazené nabídce zvolte možnost **obnovit** .

     Kliknutím na tlačítko **Obnovit vše** můžete také obnovit všechny nabídky a panely nástrojů.
