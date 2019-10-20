---
title: Režim celé obrazovky a virtuální prostor
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd3e238813c6cfd8674e5392d9ad20889e79c900
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645856"
---
# <a name="how-to-manage-editor-modes"></a>Postupy: Správa režimů editoru

Editor kódu sady Visual Studio můžete zobrazit v různých režimech zobrazení.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v tomto článku v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, například **Obecné** nebo  **C++ vizuální** nastavení, zvolte možnost **nástroje** > **Nastavení importu a exportu**a pak zvolte možnost **resetovat všechna nastavení**.

## <a name="enable-full-screen-mode"></a>Povolit režim zobrazení na celé obrazovce

Můžete zvolit, že chcete skrýt všechna okna nástrojů a zobrazit pouze okna dokumentů tím, že povolíte režim zobrazení na **celé obrazovce** .

- Stisknutím klávesy **Alt** +**SHIFT** +**ENTER** zadáte nebo ukončíte režim **zobrazení na celé obrazovce** .

     --nebo--

- Vydejte příkaz `View.Fullscreen` v **příkazovém** okně.

## <a name="enable-virtual-space-mode"></a>Povolit režim virtuálního prostoru

V režimu **virtuálního prostoru** jsou mezery vloženy na konci každého řádku kódu. Tuto možnost vyberte, pokud chcete umístit komentáře v konzistentním bodě vedle vašeho kódu.

1. V nabídce **nástroje** vyberte **možnost možnosti** .

2. Rozbalte složku **textový editor** a výběrem možnosti **všechny jazyky** nastavte globálně nebo vyberte konkrétní jazykovou složku. Chcete-li například zapnout číslování řádků pouze v Visual Basic, vyberte uzel **Basic**  > **textový editor** .

3. Vyberte **Obecné** možnosti a v části **Nastavení**vyberte **Povolit virtuální prostor**.

    > [!NOTE]
    > **Virtuální prostor** je povolený v režimu **výběru sloupce** . Pokud není režim **virtuálního prostoru** povolený, přesune se bod vložení z konce řádku přímo na první znak dalšího.

## <a name="see-also"></a>Viz také:

- [Přizpůsobení rozložení oken v aplikaci Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Písma a barvy, prostředí, dialogové okno Možnosti](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)