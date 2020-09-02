---
title: Značky Vizualizátor souběžnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 43b6115c45f9583b90711ef030834da662106f08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704355"
---
# <a name="concurrency-visualizer-markers"></a>Značky Vizualizéru souběžnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve Vizualizátor souběžnosti jsou značky označení ikony, které představují události v aplikaci.  Obvykle aplikace generuje tyto události pro určení fází nebo výskytů v aplikaci.  Události může generovat aplikace nebo knihovny a moduly runtime, které aplikace používá.  
  
## <a name="kinds-of-markers"></a>Druhy značek  
 Vizualizátor souběžnosti používá tři druhy značek k vyjádření událostí aplikace: příznaky, zprávy a rozsahy.  
  
1. Použijte *příznak* k označení zajímavého bodu v čase vaší aplikace.  Příznak můžete například použít k reprezentaci, že hodnota proměnné dosáhla určité prahové hodnoty nebo že byla vyvolána výjimka.  
  
2. *Zpráva* také označí bod v čase, ale můžete ho použít pro trasování ve stylu log.  Například to, co mohlo být v souboru protokolu dumpingové, teď můžete zalomit voláním zprávy, abyste ho mohli sledovat a zobrazit v Vizualizátor souběžnosti. K exportu těchto dat do souboru CSV můžete také použít Vizualizátor souběžnosti.  
  
3. *Rozsah* představuje časový interval ve vaší aplikaci, například jedna z jeho fází.  
  
## <a name="marker-linkage-to-threads"></a>Označení vazby na vlákna  
 Každé vlákno, které generuje značky, má samostatný kanál časové osy.  ID podprocesu, který je zodpovědný za generování událostí značky, se zobrazí vedle popisu kanálu značky.  ID, které je zobrazeno na levé straně kanálu značky, odpovídá ID jiného vlákna v aktuálním procesu.  
  
## <a name="marker-importance"></a>Důležitost značky  
 Značky můžou mít jednu ze čtyř úrovní důležitosti: nízká, Normal, vysoká a kritická.  Můžete filtrovat zdroje značek na základě úrovně důležitosti.  Pokud například chcete zobrazit pouze značky z konkrétního zdroje, který má normální nebo kritické důležitost, můžete nakonfigurovat filtr v dialogovém okně [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) . Důležitost značky se zobrazí v popisu tlačítka a v [sestavě značek](../profiling/markers-report.md).  
  
## <a name="marker-category"></a>Kategorie značek  
 Kategorie značek označuje skupinu událostí značky, které pocházejí ze stejného zdroje.  Vizualizátor souběžnosti používá barvu k odlišení různých kategorií příznaků a rozsahů. Můžete nakonfigurovat, aby Vizualizér souběžnosti používal kategorie k filtrování událostí značek od určitého poskytovatele událostí.  Pomocí dialogového okna [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) můžete nakonfigurovat filtr.  
  
## <a name="known-sources-of-markers"></a>Známé zdroje značek  
 Libovolný poskytovatel trasování událostí pro Windows může generovat značky, pokud poskytovatel dodržuje určitá omezení. Můžete nakonfigurovat Vizualizátor souběžnosti, aby naslouchal dalším zdrojům událostí pro značky. Ve výchozím nastavení naslouchá těmto zdrojům událostí:  
  
- [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)  
  
- [Task Parallel Library (TPL)](https://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23)  
  
- [Toku dat](https://msdn.microsoft.com/library/643575d0-d26d-4c35-8de7-a9c403e97dd6)  
  
- [Paralelní LINQ (PLINQ)](https://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)  
  
- [Concurrency Runtime](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)  
  
- [Podpora značek scénářů](https://msdn.microsoft.com/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
- [C++ AMP (C++ Accelerated Massive Parallelism)](https://msdn.microsoft.com/library/e27824cb-3167-409b-8c3f-a0e476d8f349)  
  
  Kartu značky v dialogovém okně [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) můžete použít k určení, zda se ve Vizualizátor souběžnosti zobrazují značky z různých zdrojů, a můžete filtrovat značky na základě důležitosti a kategorie.  
  
## <a name="markers-from-eventsource"></a>Značky z EventSource  
 Vizualizátor souběžnosti může také zobrazit události EventSource.  Další informace naleznete v tématu [Vizualizace událostí EventSource jako značek](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## <a name="see-also"></a>Viz také  
 [Značky příznaků](../profiling/flag-markers.md)   
 [Značky zpráv](../profiling/message-markers.md)   
 [Značky span](../profiling/span-markers.md)   
 [Vizualizace událostí EventSource v podobě značek](../profiling/visualizing-eventsource-events-as-markers.md)
