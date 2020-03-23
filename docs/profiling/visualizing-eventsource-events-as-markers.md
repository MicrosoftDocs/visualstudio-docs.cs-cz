---
title: Vizualizace událostí Zdroje událostí jako značek | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd6339b3f55b4a4c9a1e2c90ff3183a36f16c178
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "64811544"
---
# <a name="visualize-eventsource-events-as-markers"></a>Vizualizace událostí EventSource jako značek
Vizualizér souběžnosti může zobrazit události EventSource jako značky a můžete určit, jak se značky zobrazí. Chcete-li zobrazit značky EventSource, zaregistrujte identifikátor GUID poskytovatele ETW pomocí dialogového okna [Upřesnit nastavení.](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) Vizualizér souběžnosti má výchozí konvence představující události EventSource jako [značky příznaku](../profiling/flag-markers.md), [značky rozpětí](../profiling/span-markers.md)a [značky zpráv](../profiling/message-markers.md). Způsob zobrazení událostí EventSource můžete přizpůsobit přidáním vlastních polí k událostem. Další informace o značkách naleznete v [tématu Značky vizuálu souběžnosti](../profiling/concurrency-visualizer-markers.md). Další informace o událostech <xref:System.Diagnostics.Tracing>EventSource naleznete v tématu .

## <a name="default-visualization-of-eventsource-events"></a>Výchozí vizualizace událostí EventSource
 Ve výchozím nastavení visualizátor souběžnosti používá následující konvence k reprezentaci událostí EventSource.

### <a name="marker-type"></a>Typ značky

1. Události, které mají [Opcode](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) win:Start nebo win:Stop jsou považovány za začátek nebo konec rozpětí, resp.  Vnořené nebo překrývající se rozsahy nelze zobrazit. Dvojice událostí, které začínají na jednom vlákně a končí v jiném, nelze zobrazit.

2. Událost, jejíž Opcode není win:Start ani win:Stop je považována za příznak značky, pokud jeho [úroveň](/windows/desktop/WES/defining-severity-levels) (pole EVENT_RECORD. EVENT_HEADER. EVENT_DESCRIPTOR) je výhra:Verbose nebo vyšší.

3. Ve všech ostatních případech je událost považována za zprávu.

### <a name="importance"></a>Důležitost
 Následující tabulka definuje, jak se úroveň události mapuje na důležitost značky.

|Úroveň ETW|Význam vizualizéru souběžnosti|
|---------------|---------------------------------------|
|win:LogAlways|Normální|
|výhra:Kritická|Kritická|
|win:Chyba|Kritická|
|výhra:Upozornění|Vysoká|
|výhra:Informační|Normální|
|vyhrát:Verbose|Nízká|
|Větší než win:verbose|Nízká|

### <a name="series-name"></a>Název řady
 Název úkolu události se používá pro název řady. Název řady je prázdný, pokud pro událost nebyl definován žádný úkol.

### <a name="category"></a>Kategorie
 Pokud je úroveň win:Critical nebo win:Error, pak je kategorie Výstraha (-1). V opačném případě je kategorie výchozí (0).

### <a name="text"></a>Text
 Pokud byla pro událost definována textová zpráva formátu printf, zobrazí se jako popis značky. V opačném případě je popis název události a hodnota každého pole datové části.

## <a name="customize-visualization-of-eventsource-events"></a>Přizpůsobení vizualizace událostí EventSource
 Způsob zobrazení událostí EventSource můžete přizpůsobit přidáním příslušných polí k události, jak je popsáno v následujících částech.

### <a name="marker-type"></a>Typ značky
 Pomocí `cvType` pole, bajtu, můžete určit druh značky, která se používá k reprezentaci události. Zde jsou dostupné hodnoty pro cvType:

|cvTyp|Výsledný typ značky|
|------------------|---------------------------|
|0|Zpráva|
|1|Začátek rozpětí|
|2|Konec rozpětí|
|3|Příznak|
|Všechny ostatní hodnoty|Zpráva|

### <a name="importance"></a>Důležitost
 Toto `cvImportance` pole, bajt, můžete použít k řízení nastavení důležitosti události EventSource. Doporučujeme však řídit zobrazenou důležitost události pomocí úrovně.

|cvHodnota významu|Význam vizualizéru souběžnosti|
|------------------------|---------------------------------------|
|0|Normální|
|1|Kritická|
|2|Vysoká|
|3|Vysoká|
|4|Normální|
|5|Nízká|
|Všechny ostatní hodnoty|Nízká|

### <a name="series-name"></a>Název řady
 Pomocí `cvSeries` pole události, řetězce, můžete řídit název řady, který vizualizér souběžnosti přiděluje události EventSource.

### <a name="category"></a>Kategorie
 Pomocí `cvCategory` pole, bajt, můžete řídit kategorii, kterou vizualizér souběžnosti dává události EventSource.

### <a name="text"></a>Text
 Pomocí `cvTextW` pole, řetězec, k řízení popisu, který vizualizér souběžnosti dává události EventSource.

### <a name="spanid"></a>SpanID
 Použijte pole cvSpanId, int, aby odpovídaly dvojice událostí. Hodnota pro každou dvojici událostí start/stop, které představují rozsah, musí být jedinečná. Obvykle pro souběžný kód to vyžaduje použití synchronizačních <xref:System.Threading.Interlocked.Exchange%2A> primitiv, například k zajištění, že klíč (hodnota, která se používá pro CvSpanID) je správná.

> [!NOTE]
> Použití SpanID vnořovat rozpětí, umožnit jim částečně překrývat na stejném vlákně, nebo umožnit jim začít na jednom vlákně a konec na jiném není podporována.

## <a name="see-also"></a>Viz také
- [Značky vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md)