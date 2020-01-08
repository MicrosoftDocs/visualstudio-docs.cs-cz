---
title: Zobrazení na celé obrazovce a režim virtuálního prostoru
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77f224a6e3a1b12ed17799ddf6a2fc5c23f5d4cc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591031"
---
# <a name="how-to-manage-editor-modes"></a>Postupy: Správa režimů editoru

Editor kódu sady Visual Studio můžete zobrazit v různých režimech zobrazení.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které se zobrazí mohou lišit od těch popsaných v tomto článku v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, například k **Obecné** nebo **Visual C++** nastavení, zvolte **nástroje** > **nastavení importu a exportu**a klikněte na tlačítko **obnovit všechna nastavení**.

## <a name="enable-full-screen-mode"></a>Povolit režim zobrazení na celé obrazovce

Je možné skrýt všechna okna nástrojů a zobrazit pouze okna dokumentu tím, že **zobrazení na celé obrazovce** režimu.

- Stisknutím klávesy **Alt**+**Shift**+**Enter** a zadejte skript nebo ukončit **zobrazení na celé obrazovce** režimu.

     --nebo--

- Příkaz `View.Fullscreen` v **příkaz** okna.

## <a name="enable-virtual-space-mode"></a>Povolit režim virtuálního prostoru

V **virtuální prostor** režimu, budou vkládány mezery na konci každého řádku kódu. Vyberte tuto možnost na pozici poznámky na bod konzistentní vzhledem k vedle vašeho kódu.

1. Vyberte **možnosti** z **nástroje** nabídky.

2. Rozbalte **textový Editor** složky a zvolte **všechny jazyky** a tuto možnost nastavte, globálně nebo zvolte konkrétní jazykovou složku. Například, chcete-li zapnout čísla řádků pouze v jazyce Visual Basic, zvolte **základní** > **textový Editor** uzlu.

3. Vyberte **Obecné** možnosti a v části **nastavení**vyberte **povolit virtuální prostor**.

    > [!NOTE]
    > **Virtuální prostor** je povolený v **výběr sloupce** režimu. Když **virtuální prostor** není povolen režim, kurzor se přesune z konce jeden řádek přímo na první znak na další.

## <a name="see-also"></a>Viz také:

- [Přizpůsobení rozložení oken v sadě Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Písma a barvy, prostředí, dialogové okno Možnosti](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
