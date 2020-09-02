---
title: Tipy pro ladění vláken v nativním kódu | Microsoft Docs
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
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7c299d3585d9089f8525c2ec7f470601797cc3a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684872"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Tipy k ladění vláken v nativním kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tady je několik tipů, které můžete použít při ladění vláken v nativním kódu:  
  
- Obsah bloku informací o vlákně můžete zobrazit zadáním v okně `@TIB` **kukátka** nebo dialogovém okně **QuickWatch** .  
  
- Můžete zobrazit poslední kód chyby pro aktuální vlákno zadáním `@Err` v okně **kukátka** nebo dialogovém okně **QuickWatch** .  
  
- Funkce běhové knihovny jazyka C (CRT) mohou být užitečné pro ladění vícevláknové aplikace. Další informace najdete v tématu [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)
