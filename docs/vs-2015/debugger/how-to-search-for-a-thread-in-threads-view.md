---
title: 'Postupy: hledání vlákna v zobrazení vláken | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5974bc962faf439af8de5d50bf51bad3d824647
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64827347"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Postupy: Hledání vlákna v zobrazení vláken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Konkrétní vlákno můžete vyhledat v zobrazení vlákna pomocí jeho ID vlákna nebo řetězce modulu jako kritéria vyhledávání. Můžete také zadat počáteční směr hledání. Pole v dialogovém okně zobrazí atributy vybraného vlákna ve stromu vláken.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Hledání vlákna v zobrazení vláken  
  
1. Uspořádejte okna tak, aby se zobrazilo okno pro zobrazení Spy + + a aktivní [vlákna](../debugger/threads-view.md) .  
  
2. V nabídce **Hledat** vyberte možnost **Najít vlákno**.  
  
    Otevře se [dialogové okno hledání vláken](../debugger/thread-search-dialog-box.md) .  
  
3. Jako kritéria hledání zadejte ID vlákna nebo řetězec modulu.  
  
4. Vymažte všechna pole, pro která nechcete zadávat hodnoty.  
  
   > [!TIP]
   > Chcete-li najít všechna vlákna vlastněná modulem, zrušte zaškrtnutí políčka **vlákno** a zadejte název modulu do pole **modul** . Pak pokračujte v hledání vláken pomocí **find Next** .  
  
5. Pro počáteční směr hledání vyberte **nahoru** nebo **dolů** .  
  
6. Klikněte na **OK**.  
  
   Pokud je nalezeno vyhovující vlákno, je zvýrazněno v okně zobrazení vláken.
