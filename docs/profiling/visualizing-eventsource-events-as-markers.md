---
title: Vizualizace událostí EventSource v podobě značek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e6c28682bb6b93a2a72aaa353a2af68a9450cb9
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058588"
---
# <a name="visualize-eventsource-events-as-markers"></a>Vizualizace událostí EventSource v podobě značek
Vizualizér souběžnosti můžete zobrazit událostí EventSource jako značky a můžete řídit zobrazení značek. Chcete-li zobrazit EventSource značek, zaregistrujte zprostředkovatele trasování událostí pro Windows GUID pomocí [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno. Vizualizér souběžnosti má výchozích konvencí představují událostí EventSource jako [značky příznaků](../profiling/flag-markers.md), [značky Span](../profiling/span-markers.md), a [značky zpráv](../profiling/message-markers.md). Zobrazení událostí EventSource přidáním vlastních polí k událostem, které můžete přizpůsobit. Další informace o značkách najdete v části [značek Vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md). Další informace o událostech EventSource najdete v tématu <xref:System.Diagnostics.Tracing>.  
  
## <a name="default-visualization-of-eventsource-events"></a>Výchozí vizualizace událostí EventSource  
 Ve výchozím nastavení vizualizér souběžnosti používá k reprezentaci událostí EventSource následující konvence.  
  
### <a name="marker-type"></a>Typ značky  
  
1.  Události, které mají [Opcode](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) win: počáteční nebo win: zastavení jsou považovány za začátku nebo na konci značky span, v uvedeném pořadí.  Vnořené nebo překrývající se rozsahy nelze zobrazit. Páry událostí, které začínají na jedno vlákno a končí na jiném nelze zobrazit.  
  
2.  Událost, jejichž operační kód není win: spuštění ani win: zastavení je považován za příznak značky, pokud jeho [úroveň](/windows/desktop/WES/defining-severity-levels) (pole z EVENT_RECORD. EVENT_HEADER. EVENT_DESCRIPTOR) je win: podrobný nebo vyšší.  
  
3.  Ve všech ostatních případech je událost považována za zprávu.  
  
### <a name="importance"></a>Význam  
 Následující tabulka definuje, jak mapuje úroveň události důležitosti značky.  
  
|Úroveň trasování událostí pro Windows|Důležitost vizualizér souběžnosti|  
|---------------|---------------------------------------|  
|Win: LogAlways|Normální|  
|Win: kritické|Kritická|  
|Win: Chyba|Kritická|  
|Win: upozornění|Vysoká|  
|Win: informační|Normální|  
|Win: Verbose|Nízká|  
|Větší než win: verbose|Nízká|  
  
### <a name="series-name"></a>Název řady  
 Název úlohy události se používá pro název řady. Název řady je prázdný, pokud byla definována bez úlohy pro událost.  
  
### <a name="category"></a>Kategorie  
 Pokud se úroveň win: kritický nebo win: Chyba a potom kategorie je výstraha (-1). Kategorie, jinak je výchozí hodnota (0).  
  
### <a name="text"></a>Text  
 Pokud formátovaná textová zpráva typu printf byl definován pro událost, zobrazí se jako popis značky. Popis, jinak je název události a hodnotu každé datové pole.  
  
## <a name="customize-visualization-of-eventsource-events"></a>Přizpůsobení vizualizace událostí EventSource  
 Můžete přizpůsobit událostí EventSource zobrazení tak, že přidáte na odpovídající pole události, jak je popsáno v následujících částech.  
  
### <a name="marker-type"></a>Typ značky  
 Použití `cvType` pole bajtů, k řízení druh značky, který se používá k reprezentování události. Zde jsou k dispozici hodnoty cvType:  
  
|Hodnota cvType|Výsledný typ značky.|  
|------------------|---------------------------|  
|0|Zpráva|  
|1|Počáteční značky span|  
|2|Koncové značky span|  
|3|Příznak|  
|Všechny ostatní hodnoty|Zpráva|  
  
### <a name="importance"></a>Význam  
 Můžete použít `cvImportance` pole bajtů, řídit nastavení důležitosti EventSource událost. Doporučujeme však, kterou řídíte zobrazených význam událost pomocí jeho úroveň.  
  
|Hodnota cvImportance|Důležitost vizualizér souběžnosti|  
|------------------------|---------------------------------------|  
|0|Normální|  
|1|Kritická|  
|2|Vysoká|  
|3|Vysoká|  
|4|Normální|  
|5|Nízká|  
|Všechny ostatní hodnoty|Nízká|  
  
### <a name="series-name"></a>Název řady  
 Použití `cvSeries` pole událostí, řetězec, tak, aby název řady, umožňující vizualizér souběžnosti do událost EventSource ovládacího prvku.  
  
### <a name="category"></a>Kategorie  
 Použití `cvCategory` pole bajtů, k řízení kategorii, která vám umožní k událost EventSource vizualizér souběžnosti.  
  
### <a name="text"></a>Text  
 Použití `cvTextW` pole řetězce k řízení popis, který vizualizér souběžnosti na EventSource událost.  
  
### <a name="spanid"></a>SpanID  
 Použijte pole cvSpanId, int, tak, aby odpovídaly páry událostí. Hodnota pro každou dvojici spuštění a zastavení události, které představují rozpětí musí být jedinečný. Obvykle pro souběžné kód to vyžaduje použití primitiv synchronizace, jako <xref:System.Threading.Interlocked.Exchange%2A> zajistit, že klíč (hodnotu, která se používá pro CvSpanID) je správná.  
  
> [!NOTE]
>  Použití SpanID lze vnořit rozsahy, mohly částečně překrývat ve stejném vlákně, nebo jejich spuštění na jedno vlákno povolíte a end na jiném není podporována.  
  
## <a name="see-also"></a>Viz také:  
 [Značky vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md)