---
title: 'Postupy: použití Vizualizátoru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f981b76d471658fe82e874901ad784a17841891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778373"
---
# <a name="how-to-use-a-visualizer"></a>Postupy: Použití vizualizéru
Můžete použít Vizualizér k zobrazení obsahu proměnné nebo objektu způsobem, který je smysluplný pro datový typ. Můžete použít vizualizace z datových **tipů**, okna **kukátka** , okna **Automatické** hodnoty nebo okna **místních** hodnot.  
  
 V kompaktním rozhraní se nepodporují vizualizace.  
  
> [!NOTE]
> V aplikacích pro **Store** se podporují jenom standardní texty, HTML, XML a vizualizace JSON. Vlastní (uživatelsky vytvořené) vizualizace se nepodporují.  
  
### <a name="to-open-a-visualizer"></a>Otevření Vizualizátoru  
  
1. Klikněte na ikonu lupy, která se zobrazí vedle názvu proměnné v části **datatipů**, v okně **kukátka** nebo v okně **Automatické**kukátko, **místní**hodnoty nebo **Rychlé kukátko** .  
  
     Zobrazí se seznam vizualizují.  
  
2. Klikněte na vizualizér, který chcete použít.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Použití Vizualizátoru pro spravovaný kód při vzdáleném ladění  
  
- Před zahájením relace ladění zkopírujte knihovnu DLL Vizualizér do vzdáleného počítače.  
  
     Cesta ke knihovně DLL musí být stejná na vzdálených i místních počítačích. Tato cesta může být některá z těchto umístění:  
  
     *Cesta k instalaci sady Visual Studio*`\Common7\Packages\Debugger\Visualizers`  
  
     -nebo-  
  
     `My Documents\Visual Studio 2010\Visualizers`*Verze sady Visual Studio*`\Visualizers`  
  
## <a name="see-also"></a>Viz také  
 [Vytvořit vlastní vizualizace](../debugger/create-custom-visualizers-of-data.md)   
 [Postupy: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md)   
 [Postupy: zápis Vizualizér](../debugger/how-to-write-a-visualizer.md)   
 [Zobrazení hodnot dat v datových tipech](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)