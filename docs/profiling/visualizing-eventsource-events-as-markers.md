---
title: Vizualizace událostí EventSource jako značek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd6339b3f55b4a4c9a1e2c90ff3183a36f16c178
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811544"
---
# <a name="visualize-eventsource-events-as-markers"></a>Vizualizace událostí EventSource jako značek
Vizualizátor souběžnosti může zobrazit události EventSource jako značky a můžete určit, jak se budou značky zobrazovat. Chcete-li zobrazit značky EventSource, zaregistrujte identifikátor GUID zprostředkovatele ETW pomocí dialogového okna [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) . Vizualizátor souběžnosti má výchozí konvence pro reprezentaci událostí EventSource jako [značek příznaků](../profiling/flag-markers.md), [značek span](../profiling/span-markers.md)a [značek zpráv](../profiling/message-markers.md). Můžete přizpůsobit způsob zobrazení událostí EventSource přidáním vlastních polí do událostí. Další informace o značkách naleznete v tématu [značky Vizualizátor souběžnosti](../profiling/concurrency-visualizer-markers.md). Další informace o událostech EventSource naleznete v tématu <xref:System.Diagnostics.Tracing> .

## <a name="default-visualization-of-eventsource-events"></a>Výchozí vizualizace událostí EventSource
 Ve výchozím nastavení používá Vizualizátor souběžnosti následující konvence pro reprezentaci událostí EventSource.

### <a name="marker-type"></a>Typ značky

1. Události, které mají [opcode](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) Win: Start nebo Win: stop, jsou považovány za začátek nebo konec rozpětí, v uvedeném pořadí.  Vnořené nebo překrývající se rozpětí nelze zobrazit. Nelze zobrazit páry událostí, které začínají na jednom vlákně a končí na jiném.

2. Událost, jejíž opcode není ani Win: Start ani Win: stop se považuje za příznak značky, pokud jeho [úroveň](/windows/desktop/WES/defining-severity-levels) (pole EVENT_RECORD. EVENT_HEADER. EVENT_DESCRIPTOR) je Win: verbose nebo vyšší.

3. Ve všech ostatních případech se událost považuje za zprávu.

### <a name="importance"></a>Důležitost
 Následující tabulka definuje způsob, jakým je úroveň události mapována na důležitost značky.

|Úroveň ETW|Důležitost Vizualizátoru souběžnosti|
|---------------|---------------------------------------|
|Win: LogAlways|Normální|
|výher: kritické|Kritické|
|Win: Chyba|Kritické|
|výher: upozornění|Vysoké|
|Win: informativní|Normální|
|Win: verbose|Nízká|
|Větší než Win: verbose|Nízká|

### <a name="series-name"></a>Název řady
 Název úlohy události se používá pro název řady. Název řady je prázdný, pokud pro událost nebyla definována žádná úloha.

### <a name="category"></a>Kategorie
 Pokud se jedná o hodnotu Win: critical nebo Win: Error, kategorie je Alert (-1). V opačném případě je kategorie výchozí (0).

### <a name="text"></a>Text
 Pokud byla pro událost definována textová zpráva ve formátu printf typu, zobrazí se jako popis značky. V opačném případě je popis názvem události a hodnotou každého pole datové části.

## <a name="customize-visualization-of-eventsource-events"></a>Přizpůsobení vizualizace událostí EventSource
 Můžete přizpůsobit způsob zobrazení událostí EventSource přidáním příslušných polí do události, jak je popsáno v následujících částech.

### <a name="marker-type"></a>Typ značky
 Použijte `cvType` pole bajt pro řízení druhu značky, který se používá k reprezentaci události. Zde jsou dostupné hodnoty pro cvType:

|Hodnota cvType|Výsledný typ značky|
|------------------|---------------------------|
|0|Zpráva|
|1|Začátek rozsahu|
|2|Konec rozsahu|
|3|Příznak|
|Všechny ostatní hodnoty|Zpráva|

### <a name="importance"></a>Důležitost
 `cvImportance`Pro řízení nastavení důležitosti události EventSource můžete použít pole, bajt. Nicméně doporučujeme, abyste měli kontrolu nad zobrazeným významem události pomocí její úrovně.

|hodnota cvImportance|Důležitost Vizualizátoru souběžnosti|
|------------------------|---------------------------------------|
|0|Normální|
|1|Kritické|
|2|Vysoké|
|3|Vysoké|
|4|Normální|
|5|Nízká|
|Všechny ostatní hodnoty|Nízká|

### <a name="series-name"></a>Název řady
 Použijte `cvSeries` pole události, řetězec pro řízení názvu řady, který Vizualizér souběžnosti udělí události EventSource.

### <a name="category"></a>Kategorie
 Použijte `cvCategory` pole bajt pro řízení kategorie, kterou Vizualizér souběžnosti poskytuje události EventSource.

### <a name="text"></a>Text
 Použijte `cvTextW` pole, řetězec k řízení popisu, který Vizualizér souběžnosti udělí události EventSource.

### <a name="spanid"></a>SpanID
 Použijte pole cvSpanId (int), chcete-li spárovat dvojice událostí. Hodnota pro každou dvojici událostí spustit/zastavit, která představuje rozsah, musí být jedinečná. Obvykle pro souběžný kód vyžaduje použití primitiv synchronizace, jako <xref:System.Threading.Interlocked.Exchange%2A> je například, pro zajištění, že klíč (hodnota použitá pro CvSpanID) je správný.

> [!NOTE]
> Použití SpanID k vnořování rozsahů, umožňuje jejich částečné překrytí ve stejném vlákně nebo povolení jejich spuštění na jednom vlákně a ukončení na jiném, není podporováno.

## <a name="see-also"></a>Viz také
- [Značky Vizualizátor souběžnosti](../profiling/concurrency-visualizer-markers.md)