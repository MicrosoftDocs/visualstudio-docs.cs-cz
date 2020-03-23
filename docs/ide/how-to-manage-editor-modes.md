---
title: Režim celé obrazovky a virtuálního prostoru
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591031"
---
# <a name="how-to-manage-editor-modes"></a>Postup: Správa režimů editoru

Editor kódu sady Visual Studio můžete zobrazit v různých režimech zobrazení.

> [!NOTE]
> Zobrazená dialogová okna a příkazy nabídek se mohou lišit od těch, které jsou popsány v tomto článku, v závislosti na aktivním nastavení nebo edici. Chcete-li změnit nastavení, například **na Obecné** nebo Vizuální **nastavení c++,** zvolte **Nástroje** > **Import a export nastavení**a pak zvolte Obnovit všechna **nastavení**.

## <a name="enable-full-screen-mode"></a>Povolení režimu celé obrazovky

Povolením režimu **Na celou obrazovku** můžete skrýt všechna okna nástrojů a zobrazit pouze okna dokumentu.

- Stisknutím **klávesy Alt**+**Shift**+**Enter** přejdete do režimu Na celou obrazovku nebo jej **ukončíte.**

     -- nebo --

- Vystavte příkaz `View.Fullscreen` v okně **Příkaz.**

## <a name="enable-virtual-space-mode"></a>Povolení režimu virtuálního prostoru

V režimu **virtuálního prostoru** jsou mezery vloženy na konec každého řádku kódu. Tuto možnost vyberte, chcete-li umístit komentáře v konzistentním bodě vedle kódu.

1. Z nabídky **Nástroje** vyberte **Možnosti.**

2. Rozbalte složku **Editor textu** a zvolte **Všechny jazyky,** chcete-li tuto možnost nastavit globálně, nebo zvolte určitou jazykovou složku. Chcete-li například zapnout čísla řádků pouze v jazyce Visual Basic, zvolte uzel **Základní** > **textový editor.**

3. Vyberte **Obecné** volby a v části **Nastavení**vyberte **Povolit virtuální prostor**.

    > [!NOTE]
    > **Virtuální prostor** je povolen v režimu **výběru sloupců.** Pokud režim **virtuálního prostoru** není povolen, kurzor se přesune z konce jednoho řádku přímo na první znak dalšího.

## <a name="see-also"></a>Viz také

- [Přizpůsobení rozložení oken v sadě Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Dialogové okno Písma a barvy, Prostředí, Možnosti](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
