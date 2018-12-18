---
title: 'Postupy: přepnutí na jiné vlákno během ladění | Dokumentace Microsoftu'
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
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad13c81afc82ac69055ae117c862a1cf73b51478
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737701"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Postupy: Přepnutí na jiné vlákno během ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při ladění aplikace s více vlákny, můžete použít některou z několika metod museli přepínat kontext z vlákna, které jste pracovali jste se do jiného vlákna.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Chcete-li přepnout do libovolného vlákna, která se zobrazí v okně vlákna  
  
-   Klikněte dvakrát na vlákno.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Chcete-li přepnout na vlákno v okně zdroje  
  
-   V levém hřbetu, klikněte pravým tlačítkem na indikátor vlákna, přejděte na **přepnout na**a pak klikněte na název tohoto vlákna, do kterého chcete přejít. V místní nabídce zobrazí vlákna v tomto konkrétním umístění.  
  
     Pokud se nezobrazí žádné ukazatele, klikněte pravým tlačítkem **vlákna** okně a ověřte, že **zobrazit vlákna ve zdroji** je vybrána.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Chcete-li přepnout na vlákno na panelu nástrojů umístění ladění  
  
1.  Na **umístění ladění** nástrojů, klikněte na tlačítko **vlákna** pole.  
  
2.  V seznamu klikněte na tlačítko vlákna, do kterého chcete přejít.  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)



