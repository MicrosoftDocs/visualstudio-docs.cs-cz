---
title: Vizualizátor souběžnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 91fd9e0872529c61ffbfee42d1f3517c106340e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733824"
---
# <a name="concurrency-visualizer"></a>Vizualizér souběžnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

POZNÁMKA:]
>  Vizualizátor souběžnosti je volitelné rozšíření pro Visual Studio. Vizualizátor souběžnosti a kolekce nástrojů pro Concurrency Visualizer můžete stáhněte z následující odkazy:  
> 
> - Stáhněte si [Vizualizátor souběžnosti](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9) rozšíření.  
>   -   Stáhněte si [Concurrency Visualizer kolekce nástrojů pro Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=49103).  
> 
>   [Concurrency Visualizer nástroje příkazového řádku (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) umožňuje shromažďovat trasování z příkazového řádku, který se zobrazí ve vizualizátoru souběžnosti pro Visual Studio 2015. Nástroj můžete použít na počítačích, které nemají nainstalovanou sadu Visual Studio.  
  
 Vizualizátor souběžnosti můžete zobrazit, jak vaše aplikace s více podprocesy provádí. Zobrazení v Concurrency Visualizer poskytují grafická, tabulková a textová data, která zobrazují časové vztahy mezi vlákny v programu a systém jako celek. Vizualizátor souběžnosti můžete použít k vyhledání problémových míst výkonu, procesoru nízkého využití, kolize vlákna, migrace vlákna přes jádro, zpoždění synchronizace, rozhraní DirectX aktivity, míst překrytí I/O a dalších informací. Zobrazení obsahují data, která můžete reagovat propojením jejich grafického výstupu na volání zásobníků a zdrojový kód.  
  
 Vizualizátor souběžnosti spoléhá na [události trasování pro Windows](http://go.microsoft.com/fwlink/?LinkId=234579) funkce.  
  
> [!NOTE]
>  Vizualizátor souběžnosti nepodporuje webové projekty.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Zobrazení využití](../profiling/utilization-view.md)|Popisuje, jak zobrazit a analyzovat aktivitu systému přes všechny procesory.|  
|[Zobrazení vláken](../profiling/threads-view-parallel-performance.md)|Popisuje, jak analyzovat interakce mezi vlákny v programu.|  
|[Zobrazení jader](../profiling/cores-view.md)|Popisuje, jak analyzovat migraci vlákna mezi jádry.|  
|[Obecné vzory pro vícevláknové aplikace s nevhodným chováním](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Popisuje několik běžných vzorů a ukazuje, jak vypadají ve vizualizátoru souběžnosti.|  
|[Souběžného vývoje v sadě Visual Studio blog](http://go.microsoft.com/fwlink/?LinkId=235385)|Poskytuje tipy a osvědčené postupy pro Vizualizátor souběžnosti.|  
|[Zobrazení sestav výkonu](../profiling/performance-report-views.md)|Poskytuje referenční informace pro sestavy a zobrazení nástrojů pro profilaci Visual Studio.|  
|[SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)|Popisuje, jak použít zdrojový kód k zobrazení dalších informací ve vizualizátoru souběžnosti.|  
|[Nástroj příkazového řádku Vizualizéru souběžnosti (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Popisuje, jak používat nástroj příkazového řádku Vizualizéru souběžnosti (CVCollectionCmd.exe) ke shromažďování a zpracování trasování na počítačích, které nemáte Visual Studio.|  
  
## <a name="see-also"></a>Viz také  
 [Nástroje pro profilaci](../profiling/profiling-tools.md)



