---
title: Čas správy paměti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48cbdd523f4527af84c52366a439a18330e1828c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157352"
---
# <a name="memory-management-time"></a>Čas správy paměti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tyto segmenty na časové ose jsou přidruženy k době blokování, které jsou zařazeny do kategorie Správa paměti. To znamená, že vlákno je blokováno událostí, která je přidružena k operaci správy paměti, jako je například stránkování. Během této doby bylo vlákno blokované v rozhraní API nebo ve stavu jádra, že Vizualizátor souběžnosti se počítá jako správa paměti. Mezi ně patří události jako stránkování a přidělení paměti.  
  
 Projděte si související sestavy zásobníků volání a profil, abyste lépe pochopili základní důvody pro bloky, které jsou zařazeny do kategorie Správa paměti.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)
