---
title: Vizualizace událostí EventSource v podobě značek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c39f137299c1f229de8c3c6dc8d7329cba6033cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742559"
---
# <a name="visualizing-eventsource-events-as-markers"></a>Vizualizace událostí EventSource v podobě značek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vizualizátor souběžnosti můžete zobrazit události EventSource jako značky a můžete řídit způsob zobrazení značek. Chcete-li zobrazit značky EventSource, zaregistrujte identifikátor GUID zprostředkovatele trasování událostí pro Windows s použitím [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno. Vizualizátor souběžnosti nemá výchozí konvence pro reprezentaci událostí EventSource jako [značky příznaků](../profiling/flag-markers.md), [značky Span](../profiling/span-markers.md), a [značky zpráv](../profiling/message-markers.md). Můžete upravit způsob zobrazení událostí EventSource tak, že přidáte vlastní pole k událostem. Další informace o značkách najdete v tématu [značek Vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md). Další informace o událostí EventSource, naleznete v tématu <xref:System.Diagnostics.Tracing>.  
  
## <a name="default-visualization-of-eventsource-events"></a>Výchozí vizualizace událostí EventSource  
 Ve výchozím nastavení používá Vizualizátor souběžnosti následující konvence pro reprezentaci událostí EventSource.  
  
### <a name="marker-type"></a>Typ značky  
  
1.  Události, které mají [operační kód](http://msdn.microsoft.com/en-us/d97953df-669b-4c55-b1a8-925022b339b7) win: spuštění nebo win: zastavení jsou považovány za začátku nebo konci rozsahu, v uvedeném pořadí.  Vnořený nebo překrývající se rozsahy nelze zobrazit. Nelze zobrazit páry událostí, které v jednom vlákně začínají i končí na další.  
  
2.  Událost, jejichž operační kód není win: Start ani win: zastavení je považováno za příznak značky, pokud jeho [úroveň](http://msdn.microsoft.com/en-us/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) (pole EVENT_RECORD. EVENT_HEADER. EVENT_DESCRIPTOR) je win: podrobné nebo vyšší.  
  
3.  Ve všech ostatních případech je událost považována za zprávu.  
  
### <a name="importance"></a>Význam  
 Následující tabulka definuje, jak se úroveň události mapuje na významu značky.  
  
|Úroveň trasování událostí pro Windows|Důležitost Vizualizéru souběžnosti|  
|---------------|---------------------------------------|  
|Windows: LogAlways|Normální|  
|Vyhrajte: kritické|Kritická|  
|Windows: Chyba|Kritická|  
|Windows: upozornění|Vysoká|  
|Vyhrajte: informativní|Normální|  
|Vyhrajte: podrobné|Nízká|  
|Větší než win: podrobné|Nízká|  
  
### <a name="series-name"></a>Název řady  
 Název úlohy události se používá pro název řady. Název řady je prázdný, pokud byla definována žádná úloha pro událost.  
  
### <a name="category"></a>Kategorie  
 Pokud je úroveň win: kritický nebo win: Chyba a pak do kategorie je výstraha (-1). Kategorie, jinak je výchozí hodnota (0).  
  
### <a name="text"></a>Text  
 Pokud zpráva typu printf formátovaný text byl definován pro události, zobrazí se jako popis značky. V opačném případě se popis název události a hodnotu každé datové pole.  
  
## <a name="customizing-visualization-of-eventsource-events"></a>Přizpůsobení vizualizace událostí EventSource  
 Můžete přizpůsobit způsob událostí EventSource zobrazení tak, že přidáte do příslušných polí na událost, jak je popsáno v následujících částech.  
  
### <a name="marker-type"></a>Typ značky  
 Použití `cvType` pole bajtů, k řízení druh značky, který se používá k reprezentování události. Zde jsou dostupné hodnoty pro cvType:  
  
|Hodnota cvType|Výsledný typ značky|  
|------------------|---------------------------|  
|0|Zpráva|  
|1|Počáteční značky span|  
|2|Koncové značky span|  
|3|Příznak|  
|Všechny ostatní hodnoty|Zpráva|  
  
### <a name="importance"></a>Význam  
 Můžete použít `cvImportance` pole bajtů, k řízení nastavení důležitost události EventSource. Doporučujeme však řízení zobrazených důležitost události pomocí jeho úroveň.  
  
|Hodnota cvImportance|Důležitost Vizualizéru souběžnosti|  
|------------------------|---------------------------------------|  
|0|Normální|  
|1|Kritická|  
|2|Vysoká|  
|3|Vysoká|  
|4|Normální|  
|5|Nízká|  
|Všechny ostatní hodnoty|Nízká|  
  
### <a name="series-name"></a>Název řady  
 Použití `cvSeries` pole události, řetězce, k řízení název řady, poskytující události EventSource Vizualizátor souběžnosti.  
  
### <a name="category"></a>Kategorie  
 Použití `cvCategory` pole bajtů, k řízení kategorii, která poskytuje Vizualizátor souběžnosti události EventSource.  
  
### <a name="text"></a>Text  
 Použití `cvTextW` pole, řetězec, k řízení popis, který poskytuje Vizualizátor souběžnosti události EventSource.  
  
### <a name="spanid"></a>SpanID  
 Použijte pole cvSpanId, int, tak, aby odpovídaly páry událostí. Hodnota pro každou dvojici spuštění a zastavení událostí, které představují rozsah musí být jedinečný. Obvykle pro souběžné kódu to vyžaduje použití primitiv synchronizace, jako <xref:System.Threading.Interlocked.Exchange%2A> k ověření, že klíč (hodnota, která se používá pro CvSpanID) je správná.  
  
> [!NOTE]
>  Použití SpanID vnořit rozsahy, zajistí, aby částečně překrývají ve stejném vlákně, nebo povolit jejich spuštění v jednom vlákně a end na jiném není podporována.  
  
## <a name="see-also"></a>Viz také  
 [Značky Vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md)



