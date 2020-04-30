---
title: Vizualizátor souběžnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e7061acabbe5ce18ff6e1f210fe0003bdaf88980
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586822"
---
# <a name="concurrency-visualizer"></a>Vizualizér souběžnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ZNAČTE
> Vizualizátor souběžnosti je volitelným rozšířením sady Visual Studio. Stáhněte si nástroje Vizualizátor souběžnosti a kolekce Vizualizátor souběžnosti z následujících odkazů:  
> 
> - Stáhněte si rozšíření [Vizualizátor souběžnosti](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9) .  
>   - Stáhněte si [nástroje kolekce Vizualizátor souběžnosti pro Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103).  
> 
>   [Nástroj příkazového řádku Vizualizátor souběžnosti (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) umožňuje shromažďovat trasování z příkazového řádku, které můžete zobrazit v Vizualizátor souběžnosti pro Visual Studio 2015. Nástroj lze použít na počítačích, ve kterých není nainstalována aplikace Visual Studio.  
  
 Pomocí Vizualizátor souběžnosti můžete zjistit, jak aplikace s více vlákny funguje. Zobrazení v Vizualizér souběžnosti poskytují grafická, tabulková a textová data, která zobrazují dočasné vztahy mezi vlákny v programu a systémem jako celek. Vizualizátor souběžnosti můžete použít k vyhledání problémových míst výkonu, nevytížení procesoru, kolize vláken, migrace vláken mezi jádry, zpoždění synchronizace, aktivity rozhraní DirectX, oblastí překrytých vstupně-výstupních operací a dalších informací. Zobrazení poskytují data, která lze použít propojením jejího grafického výstupu se zásobníky volání a zdrojového kódu.  
  
 Vizualizátor souběžnosti spoléhá na [trasování událostí pro funkce Windows](https://msdn.microsoft.com/library/bb968803(VS.85).aspx) .  
  
> [!NOTE]
> Vizualizátor souběžnosti nepodporuje webové projekty.  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Zobrazení využití](../profiling/utilization-view.md)|Popisuje, jak zobrazit a analyzovat činnost systému napříč všemi procesory.|  
|[Zobrazení vláken](../profiling/threads-view-parallel-performance.md)|Popisuje, jak analyzovat interakce mezi vlákny v programu.|  
|[Zobrazení jader](../profiling/cores-view.md)|Popisuje, jak analyzovat migraci vláken napříč jádry.|  
|[Běžné vzory pro vícevláknové aplikace s nevhodným chováním](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Popisuje několik běžných vzorů a ukazuje, jak se zobrazují ve Vizualizátor souběžnosti.|  
|[Paralelní vývoj v blogu sady Visual Studio](https://docs.microsoft.com/archive/blogs/visualizeparallel/)|Poskytuje tipy a osvědčené postupy pro Vizualizátor souběžnosti.|  
|[Zobrazení sestav výkonu](../profiling/performance-report-views.md)|Poskytuje referenční informace o sestavách a zobrazeních sady Visual Studio Nástroje pro profilaci.|  
|[SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)|Popisuje, jak instrumentovat zdrojový kód pro zobrazení dalších informací v Vizualizátor souběžnosti.|  
|[Nástroj příkazového řádku Vizualizéru souběžnosti (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Popisuje, jak použít nástroj příkazového řádku Vizualizátor souběžnosti (CVCollectionCmd. exe) ke shromáždění a zpracování trasování na počítačích, které nemají aplikaci Visual Studio.|  
  
## <a name="see-also"></a>Viz také  
 [Nástroje pro profilaci](../profiling/profiling-tools.md)
