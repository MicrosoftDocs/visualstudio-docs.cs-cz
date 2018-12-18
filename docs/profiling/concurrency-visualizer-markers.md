---
title: Značky Vizualizéru souběžnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf07f939a9ce15d2ebca7afb0ee37695fa5fbf98
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220595"
---
# <a name="concurrency-visualizer-markers"></a>Značky Vizualizéru souběžnosti
Ve Vizualizátor souběžnosti značky jsou ikony, které představují událostí v aplikaci.  Aplikace obvykle generuje těchto událostí k určení fází nebo výskyty v aplikaci.  Události se můžou generovat aplikace nebo knihovny a moduly runtime, který aplikace používá.  
  
## <a name="kinds-of-markers"></a>Typy značek  
 Vizualizátor souběžnosti používá k reprezentaci události aplikace na tři typy značek: flags, zprávy a zahrnuje.  
  
1.  Použití *příznak* udávajících zajímavého bodu v čase ve vaší aplikaci.  Příznak, který může například použít k reprezentaci, že hodnota proměnné bylo dosaženo určitou prahovou hodnotu nebo že došlo k výjimce.  
  
2.  A *zpráva* značky bodu v čase, ale můžete jej také použít pro trasování protokolů – vizuální styl.  Například co může mít byly zálohované do souboru protokolu, které můžete nyní zabalit do volání zpráv tak, aby můžete zpětně a zobrazit ho ve vizualizátoru souběžnosti. Vizualizátor souběžnosti můžete použít také tato data exportovat do souboru CSV.  
  
3.  A *span* představuje ve vaší aplikaci, například jeden z jeho fází časový interval.  
  
## <a name="marker-linkage-to-threads"></a>Propojení značky vlákna  
 Každý podproces, který generuje značky má kanál časové osy.  ID vlákna, která je zodpovědná za generování značky události se zobrazí vedle popis kanálu značky.  ID, které se zobrazí na levé straně kanálu značky odpovídá ID jiného vlákna v aktuálním procesu.  
  
## <a name="marker-importance"></a>Důležitost značky  
 Značky může mít jednu ze čtyř úrovní důležitosti: Nízká, Normální, vysokou a kritické.  Můžete filtrovat zdroje značek podle úrovně závažnosti.  Například pokud chcete zobrazit značky z určitého zdroje, který má normální nebo kritický význam, můžete nakonfigurovat filtr na [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno. Důležitost značky se zobrazí v jeho popisu tlačítka a [sestava značek](../profiling/markers-report.md).  
  
## <a name="marker-category"></a>Kategorie značky  
 Kategorie značky označuje skupinu událostech, které pocházejí ze stejného zdroje.  Vizualizátor souběžnosti používá barvy k rozlišení různých kategorií příznaků a rozsahy. Vizualizátor souběžnosti filtrovat značky událostí ze zprostředkovatele určitá událost pomocí kategorií můžete nakonfigurovat.  Použití [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno filtru.  
  
## <a name="known-sources-of-markers"></a>Známých zdrojů značek  
 Jakýkoli poskytovatel trasování událostí pro Windows můžete generovat značky, tak dlouho, dokud poskytovateli dodržuje určitá omezení. Můžete nakonfigurovat tak, aby naslouchala na další událost zdroje pro značky Vizualizátor souběžnosti. Ve výchozím nastavení naslouchá na tyto zdroje událostí:  
  
- [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)  
  
- [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)  
  
- [Tok dat](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)  
  
- [Paralelní LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)  
  
- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)  
  
- [Podpora značek scénáře](/previous-versions/visualstudio/visual-studio-2010/dd984115\(v\=vs.100\))  
  
- [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)  
  
  Na kartě značky můžete použít [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno k zobrazení nebo skrytí značek z různých zdrojů ve Vizualizátor souběžnosti a vy můžete filtrovat podle značky na základě důležitosti a kategorie.  
  
## <a name="markers-from-eventsource"></a>Značky z EventSource  
 Vizualizátor souběžnosti můžete také zobrazit událostí EventSource.  Další informace najdete v tématu [událostí EventSource vizualizovat jako značky](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## <a name="see-also"></a>Viz také:  
 [Značky příznaků](../profiling/flag-markers.md)   
 [Značky zpráv](../profiling/message-markers.md)   
 [Značky rozpětí](../profiling/span-markers.md)   
 [Vizualizace událostí EventSource v podobě značek](../profiling/visualizing-eventsource-events-as-markers.md)