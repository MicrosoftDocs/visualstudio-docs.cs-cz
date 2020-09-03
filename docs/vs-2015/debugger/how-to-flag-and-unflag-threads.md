---
title: 'Postupy: příznak a odoznačení vláken | Microsoft Docs'
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
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6d6a49dd9b90172686a90d92e6b630dd70b5cf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189438"
---
# <a name="how-to-flag-and-unflag-threads"></a>Postupy: Označení a odstranění označení vlákna
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete označit vlákno, které chcete poskytnout zvláštní pozornost, a to tak, že ho označíte ikonou v podoknech **vlákna**, **paralelní zásobníky**, **paralelní kukátko**a **vlákna GPU** . Tato ikona vám může pomáhat a jiným odlišit vlákna označená příznakem z jiných vláken.  
  
 Vlákna označená příznakem také dostanou zvláštní zpracování v seznamu **vláken** na panelu nástrojů **umístění ladění** . Tento seznam může zobrazovat všechna vlákna nebo pouze vlákna označená příznakem. Při příznaku vlákna se seznam **vláken** automaticky přepíná, aby zobrazoval pouze vlákna označená příznakem, ale můžete ho přepnout zpátky a zobrazit tak všechna vlákna podle potřeby.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Označení nebo odoznačení vlákna pomocí okna vlákna  
  
- V okně **vlákna** Najděte vlákno, které vás zajímá, a kliknutím na ikonu příznak vyberte nebo zrušte zaškrtnutí tohoto příznaku.  
  
### <a name="to-unflag-all-threads"></a>Chcete-li zrušit označení všech vláken  
  
- V okně **vlákna** klikněte pravým tlačítkem na libovolné vlákno a pak klikněte na zrušit **označení všech vláken**.  
  
### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem  
  
- V okně ladění vyberte tlačítko příznak.  
  
### <a name="to-flag-just-my-code"></a>Označení Pouze můj kód  
  
1. Na panelu nástrojů v horní části okna **vlákna** klikněte na ikonu příznak.  
  
2. V rozevíracím seznamu klikněte na **příznak pouze můj kód**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Označení vláken, která jsou přidružena k vybraným modulům  
  
1. Na panelu nástrojů okna **vlákna** klikněte na ikonu příznak.  
  
2. V rozevíracím seznamu klikněte na možnost **Označit vlastní výběr modulu**.  
  
3. V dialogovém okně **Vybrat moduly** vyberte moduly, které chcete.  
  
4. Volitelné Do **vyhledávacího** pole zadejte řetězec, který bude hledat konkrétní moduly.  
  
5. Klikněte na **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Návod: Ladění vícevláknové aplikace](../debugger/walkthrough-debugging-a-multithreaded-application.md)
