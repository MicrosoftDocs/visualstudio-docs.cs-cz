---
title: 'Postupy: označení a odstranění označení vlákna | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 5816007476da56321e58182e636b54a5a5697994
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817487"
---
# <a name="how-to-flag-and-unflag-threads"></a>Postupy: Označení a odstranění označení vlákna
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete označit příznakem vlákna, které chcete věnovat zvláštní pozornost označením s ikonou v **vlákna**, **paralelní zásobníky**, **paralelní sledování**, a **GPU Vlákna** systému windows. Tato ikona vám může pomoct a ostatní vlákna s příznakem odlišili od ostatních vláken.  
  
 Vlákna s příznaky také přijímat zvláštní zacházení v **vlákna** seznamu **umístění ladění** nástrojů. Tento seznam můžete zobrazit všechna vlákna nebo pouze vlákna s příznakem. Když Označit vlákno, **vlákno** seznamu, automaticky se přepne na Zobrazit pouze vlákna s příznakem, ale můžete přepnout zpět na Zobrazit všechna vlákna podle potřeby.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Chcete-li označit nebo zrušit označení vlákna pomocí okna vlákna  
  
-   V **vlákna** okně Najít vlákno, které vás zajímají a kliknutím na ikonu příznaku zaškrtněte nebo zrušte příznak.  
  
### <a name="to-unflag-all-threads"></a>Chcete-li odznačit všechna vlákna  
  
-   V **vlákna** okna, klikněte pravým tlačítkem na libovolného vlákna a pak klikněte na **odznačit všechna vlákna**.  
  
### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem  
  
-   Klikněte na tlačítko příznak v okně ladění.  
  
### <a name="to-flag-just-my-code"></a>Chcete-li označit jen můj kód  
  
1.  Na panelu nástrojů v horní části **vlákna** okna, klikněte na ikonu vlajky.  
  
2.  V rozevíracím seznamu, klikněte na tlačítko **příznak funkce pouze můj kód**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>K nastavení příznaku vláken, které jsou spojeny s vybrané moduly  
  
1.  Na panelu nástrojů **vlákna** okna, klikněte na ikonu vlajky.  
  
2.  V rozevíracím seznamu, klikněte na tlačítko **volba vlastního modulu příznaků**.  
  
3.  V **vyberte moduly** dialogového okna, vyberte moduly, které chcete.  
  
4.  (Volitelné) V **hledání** zadejte řetězec k vyhledání konkrétních modulů.  
  
5.  Klikněte na tlačítko **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Návod: Ladění vícevláknové aplikace](../debugger/walkthrough-debugging-a-multithreaded-application.md)



