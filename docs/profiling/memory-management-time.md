---
title: Čas správy paměti | Microsoft Docs
description: Zjistěte, jak tento scénář znamená, že vlákno je blokováno událostí, která je přidružena k operaci správy paměti, jako je například stránkování.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad3c913e6c983749e53940f5e75ad3bdba48bf92
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873629"
---
# <a name="memory-management-time"></a>Čas správy paměti
Tyto segmenty na časové ose jsou přidruženy k době blokování, které jsou zařazeny do kategorie Správa paměti. Tento scénář znamená, že vlákno je blokováno událostí, která je přidružena k operaci správy paměti, jako je například stránkování. Během této doby bylo vlákno blokované v rozhraní API nebo ve stavu jádra, že Vizualizátor souběžnosti se počítá jako správa paměti. Mezi ně patří události jako stránkování a přidělení paměti.

 Projděte si související sestavy zásobníků volání a profil, abyste lépe pochopili základní důvody pro bloky, které jsou zařazeny do kategorie Správa paměti.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)