---
title: Přizpůsobení nabídek a panelů nástrojů
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb58d0a20e8764e7cefe013458476ddcd41ac416
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049688"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Postupy: přizpůsobení nabídek a panelů nástrojů v sadě Visual Studio

Visual Studio můžete přizpůsobit nejen přidáváním a odebíráním nabídky na řádku nabídek a panelů nástrojů, ale také přidáte nebo odeberete příkazy na daném panelu nástrojů nebo nabídce.

> [!WARNING]
> Po přizpůsobení panelu nástrojů nebo nabídky, ujistěte se, že jeho zaškrtávací políčko zaškrtnuto v **vlastní** dialogové okno. V opačném případě se vaše změny po ukončení a opětovném spuštění sady Visual Studio nezachovají.

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Přidání, odebrání nebo přesunutí nabídky na řádku nabídek

1.  V panelu nabídky zvolte **nástroje** > **vlastní**.

     **Vlastní** zobrazí se dialogové okno.

2.  Na **příkazy** kartu, ponechte **nabídek** vybraný přepínač, ponechte **nabídek** vybrán v seznamu vedle této možnosti a pak proveďte jednu z následujících sad pomocí následujících kroků:

    -   Chcete-li přidat nabídku, zvolte **přidat novou nabídku** tlačítko, zvolte **změnit výběr** tlačítko a pak zadejte název nabídky, kterou chcete přidat.

        ![Ukazuje, jak přidat nabídku dialogové okno přizpůsobit](../ide/media/addmenu.png)

    -   Chcete-li nabídku odebrat, zvolte jej v **ovládací prvky** seznamu a klikněte na tlačítko **odstranit** tlačítko.

    -   Přejděte do nabídky v rámci řádku nabídek zvolte z nabídky **ovládací prvky** seznamu a klikněte na tlačítko **přesunout nahoru** nebo **přesunout dolů** tlačítko.

## <a name="add-remove-or-move-a-toolbar"></a>Přidání, odebrání nebo přesunutí panelu nástrojů

1.  V panelu nabídky zvolte **nástroje** > **vlastní**.

     **Vlastní** zobrazí se dialogové okno.

2.  Na **nástrojů** kartu, proveďte jednu z následujících sad kroků:

    -   Chcete-li přidat panel nástrojů, zvolte **nový** tlačítko, zadejte název panelu nástrojů, které chcete přidat a potom klikněte **OK** tlačítko.

        ![Přizpůsobení dialogové okno ukazující, jak přidat panel nástrojů](../ide/media/addtoolbar.png)

    -   Chcete-li vlastní panel nástrojů odebrat, zvolte jej v **panely nástrojů** seznamu a klikněte na tlačítko **odstranit** tlačítko.

        > [!IMPORTANT]
        > Můžete odstranit panely nástrojů, které vytvoříte, ale ne výchozí panely nástrojů.

    -   Chcete-li přesunout do jiné umístění ukotvení panelu nástrojů, zvolte jej v **panely nástrojů** klikněte na položku **změnit výběr** tlačítko a pak v zobrazeném seznamu zvolte umístění.

        Panel nástrojů můžete také přetáhnout pomocí jeho levého okraje na libovolné místo v hlavní oblasti ukotvení.

        > [!NOTE]
        > Další informace o možnostech zlepšení použitelnosti a přístupnosti panelů nástrojů naleznete v tématu [jak: Možnosti usnadnění přístupu IDE nastavit](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name="customizing_menu">Přizpůsobení nabídky nebo panelu nástrojů</a>

1.  V panelu nabídky zvolte **nástroje** > **vlastní**.

    **Vlastní** zobrazí se dialogové okno.

2.  Na **příkazy** kartu, zvolte přepínač pro typ prvku, který chcete upravit.

3.  V seznamu pro daný typ prvku zvolte nabídku nebo panel nástrojů, který chcete upravit, a pak proveďte jednu z následujících skupin kroků:

    -   Chcete-li přidat příkaz, zvolte **přidat příkaz** tlačítko.

        V **přidat příkaz** dialogového okna zvolte položku v **kategorie** , zvolte položku v **příkazy** seznamu a klikněte na tlačítko **OK**tlačítko.

        ![Příkaz dialogové okno Přidat v sadě Visual Studio](../ide/media/addcommand.png)

    -   Chcete-li příkaz odstranit, zvolte jej v **ovládací prvky** seznamu a klikněte na tlačítko **odstranit** tlačítko.

    -   Chcete-li změnit pořadí příkazů, zvolte příkaz v **ovládací prvky** seznamu a klikněte na tlačítko **nahoru** nebo **přesunout dolů** tlačítko.

    -   Pro skupinu příkazů v rámci vodorovnou horizontální čáru, vyberte první příkaz v **ovládací prvky** klikněte na položku **změnit výběr** tlačítko a pak zvolte **začít vytvářet skupinu** v Zobrazí se nabídka.

## <a name="reset-a-menu-or-a-toolbar"></a>Obnovení nabídky nebo panelu nástrojů

1.  V panelu nabídky zvolte **nástroje** > **vlastní**.

    **Vlastní** zobrazí se dialogové okno.

2.  Na **příkazy** kartu, zvolte přepínač pro typ prvku, který chcete obnovit.

3.  V seznamu pro daný typ prvku zvolte nabídku nebo panel nástrojů, které chcete obnovit.

4.  Zvolte **změnit výběr** tlačítko a pak zvolte **resetování** v zobrazené nabídce.

    Můžete také obnovit všechny nabídky a panely nástrojů výběrem **Obnovit vše** tlačítko.

## <a name="see-also"></a>Viz také:

- [Přizpůsobení integrovaného vývojového prostředí](../ide/personalizing-the-visual-studio-ide.md)
- [Přizpůsobení editoru](../ide/customizing-the-editor.md)