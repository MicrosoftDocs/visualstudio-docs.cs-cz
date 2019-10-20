---
title: 'Postupy: Správa režimů editoru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a188e90d3feeb903eb8b4efceb91eb53cac3bdce
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651851"
---
# <a name="how-to-manage-editor-modes"></a>Postupy: Správa režimů editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor Visual Studio Code můžete zobrazit v různých režimech zobrazení.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="enabling-full-screen-mode"></a>Povolení režimu zobrazení na celé obrazovce
 Můžete zvolit, že chcete skrýt všechna okna nástrojů a zobrazit pouze okna dokumentů tím, že povolíte režim zobrazení na **celé obrazovce** .

#### <a name="to-enable-full-screen-mode"></a>Postup zapnutí režimu zobrazení na celé obrazovce

- Stisknutím kombinace kláves ALT + SHIFT + ENTER zadáte nebo ukončete režim **zobrazení na celé obrazovce** .

     --nebo--

- Vydejte příkaz `View.Fullscreen` v **příkazovém** okně.

## <a name="enabling-virtual-space-mode"></a>Povoluje se režim virtuálního prostoru.
 V režimu **virtuálního prostoru** jsou mezery vloženy na konci každého řádku kódu. Tuto možnost vyberte, pokud chcete umístit komentáře v konzistentním bodě vedle vašeho kódu.

#### <a name="to-enable-virtual-space-mode"></a>Postup povolení režimu virtuálního prostoru

1. V nabídce **nástroje** vyberte **možnost možnosti** .

2. Rozbalte složku **textový editor** a výběrem možnosti **všechny jazyky** nastavte globálně nebo vyberte konkrétní jazykovou složku. (Chcete-li například zapnout číslování řádků pouze v Visual Basic, vyberte možnost základní, textový editor.)

3. Vyberte **Obecné** možnosti a v části **Nastavení**vyberte **Povolit virtuální prostor**.

    > [!NOTE]
    > **Virtuální prostor** je povolený v režimu **výběru sloupce** . Pokud není režim **virtuálního prostoru** povolený, přesune se bod vložení z konce řádku přímo na první znak dalšího.

## <a name="see-also"></a>Viz také
 [Přizpůsobení editoru](../ide/customizing-the-editor.md) , [Jak: uspořádat a ukotvit Windows](../misc/how-to-arrange-and-dock-windows.md) [písma a barvy, prostředí, dialogové okno Možnosti](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
