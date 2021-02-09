---
title: Použití Vizualizátoru stromu WPF | Microsoft Docs
description: Použijte Vizualizér Windows Presentation Foundation (WPF) k prozkoumání vizuálního stromu objektu WPF a k zobrazení vlastností závislosti WPF v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7515ec4aff82bc334c712360969c5f0414e1998a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926519"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Postupy: Použití vizualizéru stromu WPF
Můžete použít Vizualizér stromu WPF k prozkoumání vizuálního stromu objektu WPF a k zobrazení vlastností závislosti WPF pro objekty, které jsou obsaženy v tomto stromu. Další informace o vizuálních stromech naleznete [v tématu stromy v](/dotnet/framework/wpf/advanced/trees-in-wpf)subsystému WPF. Další informace o vlastnostech závislosti najdete v tématu [Přehled vlastností závislosti](/dotnet/framework/wpf/advanced/dependency-properties-overview).

 Když otevřete Vizualizér stromu WPF, zobrazí se dvě podokna: **vizuální strom** na levé straně a **vlastnosti** _název_**:**_typ_ na pravé straně. V podokně **vizuálního stromu** vyberte libovolný objekt a **vlastnosti** _název_**:** podokno _typ_ je automaticky aktualizováno, aby se zobrazily vlastnosti daného objektu.

 > [!NOTE]
 > Můžete také použít [živý vizuální strom a živý Průzkumník vlastností](../xaml-tools/inspect-xaml-properties-while-debugging.md) k prohlédnutí vizuálního stromu objektů WPF. Vizualizér stromu WPF je starší funkce a není v aktivním vývoji.

### <a name="to-open-the-wpf-tree-visualizer"></a>Otevření Vizualizér stromu WPF

1. V okně DataTip, okno **kukátka** , okno **Automatické** hodnoty a okno **místní** hodnoty vedle názvu objektu WPF klikněte na šipku vedle ikony lupy.

     Zobrazí se seznam vizualizují.

2. Klikněte na **Vizualizér stromu WPF**.

### <a name="to-search-the-visual-tree"></a>Hledání ve vizuálním stromu

- Do **vyhledávacího** pole zadejte řetězec, který chcete vyhledat, v podokně **vizuální strom** .

  Vizualizér stromu WPF okamžitě vyhledá první objekt ve vizuálním stromu, který odpovídá zadanému řetězci. Zadáním více znaků získáte přesnější shodu.

  - Chcete-li přejít k další shodě ve vizuálním stromu, klikněte na tlačítko **Další**.

  - Pokud se chcete vrátit k předchozí shodě, klikněte na **Předchozí**.

  - Chcete-li vymazat kritéria hledání, klikněte na tlačítko **Vymazat**.

### <a name="to-search-the-properties-list"></a>Hledání v seznamu vlastností

- V podokně **vlastnosti** _názvu_**:**_typ_ zadejte řetězec, který chcete v poli **filtru** vyhledat.

  Vizualizér stromu WPF ihned vyhledá vlastnosti, které odpovídají řetězci, který jste zadali; Nyní se v seznamu zobrazí pouze vlastnosti, které odpovídají řetězci, který jste zadali. Zadáním více znaků získáte přesnější shodu.

  - Chcete-li vymazat kritéria hledání, klikněte na tlačítko **Vymazat**.

### <a name="to-close-the-visualizer"></a>Zavření Vizualizér

- Klikněte na ikonu **Zavřít** v pravém horním rohu dialogového okna.

## <a name="see-also"></a>Viz také
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
- [Stromy v subsystému WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Přehled vlastností závislosti](/dotnet/framework/wpf/advanced/dependency-properties-overview)
