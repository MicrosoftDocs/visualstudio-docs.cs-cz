---
title: 'Postupy: použití Vizualizátoru stromu WPF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 381dc45351ae03e615afbdd31239869e3dba8e4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825438"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Postupy: Použití vizualizéru stromu WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít Vizualizér stromu WPF k prozkoumání vizuálního stromu objektu WPF a k zobrazení vlastností závislosti WPF pro objekty, které jsou obsaženy v tomto stromu. Další informace o vizuálních stromech naleznete [v tématu stromy v](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)subsystému WPF. Další informace o vlastnostech závislosti najdete v tématu [Přehled vlastností závislosti](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
 Když otevřete Vizualizér stromu WPF, zobrazí se dvě podokna: **vizuální strom** na levé straně a **vlastnosti** _název_**:**_typ_ na pravé straně. V podokně **vizuálního stromu** vyberte libovolný objekt a **vlastnosti** _název_**:** podokno_typ_ je automaticky aktualizováno, aby se zobrazily vlastnosti daného objektu.  
  
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
 [Postupy: použití Vizualizátoru](../misc/how-to-use-a-visualizer.md)   
 [Vytvořit vlastní vizualizace](../debugger/create-custom-visualizers-of-data.md)   
 [Stromy v subsystému WPF](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [Přehled vlastností závislosti](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)
