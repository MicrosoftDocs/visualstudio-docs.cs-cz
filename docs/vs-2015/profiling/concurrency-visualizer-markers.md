---
title: Značky Vizualizéru souběžnosti | Dokumentace Microsoftu
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
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fa2a57d08f2b86fec573f02129a326907e3e3a9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790445"
---
# <a name="concurrency-visualizer-markers"></a>Značky Vizualizéru souběžnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
- [Task Parallel Library (TPL)](http://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23)  
  
- [Tok dat](http://msdn.microsoft.com/library/643575d0-d26d-4c35-8de7-a9c403e97dd6)  
  
- [Paralelní LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)  
  
- [Concurrency Runtime](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)  
  
- [Podpora značek scénáře](http://msdn.microsoft.com/en-us/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
- [C++ AMP (C++ Accelerated Massive Parallelism)](http://msdn.microsoft.com/library/e27824cb-3167-409b-8c3f-a0e476d8f349)  
  
  Na kartě značky můžete použít [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno k zobrazení nebo skrytí značek z různých zdrojů ve Vizualizátor souběžnosti a vy můžete filtrovat podle značky na základě důležitosti a kategorie.  
  
## <a name="markers-from-eventsource"></a>Značky z EventSource  
 Vizualizátor souběžnosti můžete také zobrazit událostí EventSource.  Další informace najdete v tématu [vizualizace událostí EventSource v podobě značek](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## <a name="see-also"></a>Viz také  
 [Značky příznaků](../profiling/flag-markers.md)   
 [Značky zpráv](../profiling/message-markers.md)   
 [Značky rozpětí](../profiling/span-markers.md)   
 [Vizualizace událostí EventSource v podobě značek](../profiling/visualizing-eventsource-events-as-markers.md)



