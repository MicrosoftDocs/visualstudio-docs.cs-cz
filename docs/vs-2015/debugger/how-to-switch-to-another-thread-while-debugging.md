---
title: 'Postupy: přepnutí na jiné vlákno během ladění | Microsoft Docs'
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
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f481a0b1cb2142dc7dbfe11e17ac627753cebf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176511"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Postupy: Přepnutí na jiné vlákno během ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při ladění vícevláknové aplikace můžete použít některou z několika metod k přepnutí kontextu z vlákna, se kterým jste pracovali, s jiným vláknem.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Přepnutí na jakékoli vlákno, které se zobrazí v okně vlákna  
  
- Dvakrát klikněte na vlákno.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Přepnutí na vlákno v okně zdrojového kódu  
  
- V levém hřbetu klikněte pravým tlačítkem myši na indikátor vlákna, přejděte na příkaz **Přepnout na**a potom klikněte na název vlákna, na které chcete přepnout. Místní nabídka zobrazuje pouze vlákna na daném konkrétním místě.  
  
     Pokud se nezobrazí žádné indikátory, klikněte pravým tlačítkem myši v okně **vlákna** a ověřte, zda je vybrána možnost **Zobrazit vlákna ve zdroji** .  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Přepnutí na vlákno na panelu nástrojů umístění ladění  
  
1. Na panelu nástrojů **umístění ladění** klikněte na pole **vlákno** .  
  
2. V seznamu klikněte na vlákno, na které chcete přepnout.  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
