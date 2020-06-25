---
title: Přizpůsobení nabídek a panelů nástrojů
ms.date: 11/04/2016
ms.topic: how-to
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed85d3a3406cf7abf4bc08e728cc647d605e16ae
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284396"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Postupy: přizpůsobení nabídek a panelů nástrojů v aplikaci Visual Studio

Aplikaci Visual Studio můžete přizpůsobit nejen přidáním a odebráním panelů nástrojů a nabídek na panelu nabídek, ale také přidáním a odebráním příkazů na libovolném daném panelu nástrojů nebo v nabídce.

> [!WARNING]
> Po přizpůsobení panelu nástrojů nebo nabídky se ujistěte, že jeho zaškrtávací políčko zůstane zaškrtnuté v dialogovém okně **přizpůsobit** . V opačném případě se vaše změny po ukončení a opětovném spuštění sady Visual Studio nezachovají.

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Přidání, odebrání nebo přesunutí nabídky na řádku nabídek

1. Na řádku nabídek klikněte na **nástroje**  >  **přizpůsobit**.

     Otevře se dialogové okno **přizpůsobit** .

2. Na kartě **příkazy** ponechte vybraný přepínač **panelu nabídek** , v seznamu vedle této možnosti vyberte **panel nabídek** a pak proveďte jednu z následujících sad kroků:

    - Chcete-li přidat nabídku, klikněte na tlačítko **Přidat novou nabídku** , klikněte na tlačítko **změnit výběr** a potom zadejte název nabídky, kterou chcete přidat.

        ![Dialogové okno přizpůsobit, které ukazuje, jak přidat nabídku](../ide/media/addmenu.png)

    - Pokud chcete nabídku odebrat, zvolte ji v seznamu **ovládací prvky** a klikněte na tlačítko **Odstranit** .

    - Chcete-li přesunout nabídku v rámci řádku nabídek, zvolte nabídku v seznamu **ovládací prvky** a potom klikněte na tlačítko **Přesunout nahoru** nebo **Přesunout dolů** .

## <a name="add-remove-or-move-a-toolbar"></a>Přidání, odebrání nebo přesunutí panelu nástrojů

1. Na řádku nabídek klikněte na **nástroje**  >  **přizpůsobit**.

     Otevře se dialogové okno **přizpůsobit** .

2. Na kartě **panel nástrojů** proveďte jednu z následujících sad kroků:

    - Chcete-li přidat panel nástrojů, klikněte na tlačítko **Nový** , zadejte název panelu nástrojů, který chcete přidat, a poté klikněte na tlačítko **OK** .

        ![Dialogové okno přizpůsobit, které ukazuje, jak přidat panel nástrojů](../ide/media/addtoolbar.png)

    - Chcete-li odebrat vlastní panel nástrojů, zvolte jej v seznamu **panely nástrojů** a pak klikněte na tlačítko **Odstranit** .

        > [!IMPORTANT]
        > Můžete odstranit panely nástrojů, které vytvoříte, ale ne výchozí panely nástrojů.

    - Chcete-li přesunout panel nástrojů do jiného umístění ukotvení, zvolte jej v seznamu **panely nástrojů** , klikněte na tlačítko **změnit výběr** a potom zvolte umístění v seznamu, který se zobrazí.

        Panel nástrojů můžete také přetáhnout pomocí jeho levého okraje na libovolné místo v hlavní oblasti ukotvení.

        > [!NOTE]
        > Další informace o tom, jak zlepšit použitelnost a přístupnost panelů nástrojů, naleznete v tématu [How to: set a ACCESSIBILITY IDE Options](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name=""></a><a name="customizing_menu">Přizpůsobení nabídky nebo panelu nástrojů</a>

1. Na řádku nabídek klikněte na **nástroje**  >  **přizpůsobit**.

    Otevře se dialogové okno **přizpůsobit** .

2. Na kartě **příkazy** klikněte na tlačítko možností pro typ prvku, který chcete přizpůsobit.

3. V seznamu pro daný typ prvku zvolte nabídku nebo panel nástrojů, který chcete upravit, a pak proveďte jednu z následujících skupin kroků:

    - Chcete-li přidat příkaz, klikněte na tlačítko **Přidat příkaz** .

        V dialogovém okně **Přidat příkaz** zvolte položku v seznamu **kategorie** , zvolte položku v seznamu **příkazy** a pak klikněte na tlačítko **OK** .

        ![Dialogové okno Přidat příkaz v aplikaci Visual Studio](../ide/media/addcommand.png)

    - Pokud chcete příkaz Odstranit, vyberte ho v seznamu **ovládací prvky** a pak klikněte na tlačítko **Odstranit** .

    - Chcete-li změnit pořadí příkazů, zvolte příkaz v seznamu **ovládací prvky** a potom klikněte na tlačítko **Přesunout nahoru** nebo **Přesunout dolů** .

    - Chcete-li seskupit příkazy pod vodorovnou čárou, zvolte první příkaz v seznamu **ovládací prvky** , klikněte na tlačítko **změnit výběr** a potom v zobrazené nabídce zvolte možnost **zahájit skupinu** .

## <a name="reset-a-menu-or-a-toolbar"></a>Resetování nabídky nebo panelu nástrojů

1. Na řádku nabídek klikněte na **nástroje**  >  **přizpůsobit**.

    Otevře se dialogové okno **přizpůsobit** .

2. Na kartě **příkazy** klikněte na tlačítko možností pro typ prvku, který chcete obnovit.

3. V seznamu pro daný typ prvku zvolte nabídku nebo panel nástrojů, které chcete obnovit.

4. Klikněte na tlačítko **změnit výběr** a potom v zobrazené nabídce zvolte možnost **obnovit** .

    Kliknutím na tlačítko **Obnovit vše** můžete také obnovit všechny nabídky a panely nástrojů.

## <a name="see-also"></a>Viz také

- [Přizpůsobení integrovaného vývojového prostředí](../ide/personalizing-the-visual-studio-ide.md)
- [Přizpůsobení editoru](../ide/how-to-change-text-case-in-the-editor.md)
