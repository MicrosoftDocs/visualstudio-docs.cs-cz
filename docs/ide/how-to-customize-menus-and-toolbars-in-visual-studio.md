---
title: Přizpůsobení nabídek a panelů nástrojů
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed425b120d5d47fb684294ce17bd7d48374c638e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301851"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Postup: Přizpůsobení nabídek a panelů nástrojů v sadě Visual Studio

Aplikaci Visual Studio můžete přizpůsobit nejen přidáním a odebráním panelů nástrojů a nabídek na panelu nabídek, ale také přidáním a odebráním příkazů na libovolném panelu nástrojů nebo nabídce.

> [!WARNING]
> Po přizpůsobení panelu nástrojů nebo nabídky zkontrolujte, zda jeho zaškrtávací políčko zůstane zaškrtnuto v dialogovém okně **Přizpůsobit.** V opačném případě se vaše změny po ukončení a opětovném spuštění sady Visual Studio nezachovají.

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Přidání, odebrání nebo přesunutí nabídky na řádku nabídek

1. Na řádku nabídek zvolte **Přizpůsobit nástroje** > **.**

     Otevře se dialogové okno **Přizpůsobit.**

2. Na kartě **Příkazy** ponechte vybrané tlačítko **volby Panel nabídek,** ponechejte **panel nabídek** vybraný v seznamu vedle této možnosti a proveďte jednu z následujících sad kroků:

    - Chcete-li přidat nabídku, zvolte tlačítko **Přidat novou nabídku,** zvolte tlačítko **Změnit výběr** a pojmenujte nabídku, kterou chcete přidat.

        ![Dialogové okno Přizpůsobit způsob přidání nabídky](../ide/media/addmenu.png)

    - Chcete-li nabídku odebrat, zvolte ji v seznamu **Ovládací prvky** a pak zvolte tlačítko **Odstranit.**

    - Chcete-li přesunout nabídku v řádku nabídek, zvolte nabídku v seznamu **Ovládací prvky** a pak zvolte tlačítko **Přesunout nahoru** nebo **Přesunout dolů.**

## <a name="add-remove-or-move-a-toolbar"></a>Přidání, odebrání nebo přesunutí panelu nástrojů

1. Na řádku nabídek zvolte **Přizpůsobit nástroje** > **.**

     Otevře se dialogové okno **Přizpůsobit.**

2. Na kartě **Panel nástrojů** proveďte jednu z následujících sad kroků:

    - Chcete-li přidat panel nástrojů, zvolte tlačítko **Nový,** zadejte název panelu nástrojů, který chcete přidat, a pak zvolte tlačítko **OK.**

        ![Dialogové okno Přizpůsobit způsob přidání panelu nástrojů](../ide/media/addtoolbar.png)

    - Chcete-li odstranit vlastní panel nástrojů, zvolte ho v seznamu **Panely nástrojů** a pak zvolte tlačítko **Odstranit.**

        > [!IMPORTANT]
        > Můžete odstranit panely nástrojů, které vytvoříte, ale ne výchozí panely nástrojů.

    - Chcete-li panel nástrojů přesunout do jiného umístění ukotvení, zvolte jej v seznamu **Panely nástrojů,** zvolte tlačítko **Změnit výběr** a pak zvolte umístění v seznamu, který se zobrazí.

        Panel nástrojů můžete také přetáhnout pomocí jeho levého okraje na libovolné místo v hlavní oblasti ukotvení.

        > [!NOTE]
        > Další informace o tom, jak zlepšit použitelnost a usnadnění používání panelů nástrojů, naleznete v tématu [Postup: Nastavení možností usnadnění přístupu pomocí ide](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name=""></a><a name="customizing_menu">Přizpůsobení nabídky nebo panelu nástrojů</a>

1. Na řádku nabídek zvolte **Přizpůsobit nástroje** > **.**

    Otevře se dialogové okno **Přizpůsobit.**

2. Na kartě **Příkazy** zvolte přepínač pro typ prvku, který chcete přizpůsobit.

3. V seznamu pro daný typ prvku zvolte nabídku nebo panel nástrojů, který chcete upravit, a pak proveďte jednu z následujících skupin kroků:

    - Chcete-li přidat příkaz, zvolte tlačítko **Přidat příkaz.**

        V dialogovém okně **Přidat příkaz** zvolte položku v seznamu **Kategorie,** zvolte položku v seznamu **Příkazy** a pak zvolte tlačítko **OK.**

        ![Dialogové okno Přidat příkaz v Sadě Visual Studio](../ide/media/addcommand.png)

    - Chcete-li příkaz odstranit, zvolte ho v seznamu **Ovládací prvky** a pak zvolte tlačítko **Odstranit.**

    - Chcete-li příkazy uřadit, zvolte příkaz v seznamu **Ovládací prvky** a pak zvolte tlačítko **Přesunout nahoru** nebo **Přesunout dolů.**

    - Chcete-li seskupit příkazy pod vodorovnou čarou, zvolte první příkaz v seznamu **Ovládací prvky,** zvolte tlačítko **Změnit výběr** a pak v nabídce, která se zobrazí, zvolte **Zahájit skupinu.**

## <a name="reset-a-menu-or-a-toolbar"></a>Obnovení nabídky nebo panelu nástrojů

1. Na řádku nabídek zvolte **Přizpůsobit nástroje** > **.**

    Otevře se dialogové okno **Přizpůsobit.**

2. Na kartě **Příkazy** zvolte přepínač pro typ prvku, který chcete resetovat.

3. V seznamu pro daný typ prvku zvolte nabídku nebo panel nástrojů, které chcete obnovit.

4. Zvolte **tlačítko Změnit výběr** a pak v nabídce, která se zobrazí, zvolte **Obnovit.**

    Můžete také obnovit všechny nabídky a panely nástrojů výběrem tlačítka **Obnovit vše.**

## <a name="see-also"></a>Viz také

- [Přizpůsobení prostředí IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Přizpůsobení editoru](../ide/how-to-change-text-case-in-the-editor.md)
