---
title: Dialogové okno Upřesnit nastavení (vizualizér souběžnosti) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa9d6658ae14c4b84aae9361f73e4701e758f975
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72911226"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Dialogové okno Upřesnit nastavení (Vizualizátor souběžnosti)
Pomocí dialogového okna **Upřesnit nastavení** ve vizualizéru souběžnosti můžete řídit způsob shromažďování trasování.  Dialogové okno obsahuje karty pro symboly, Jen můj kód, ukládání do vyrovnávací paměti, filtrování, clr události, značky, zprostředkovatele a soubory.

## <a name="symbols"></a>Symboly
 Vizualizér souběžnosti používá stejné nastavení symbolu jako ladicí program visual studia. Vizualizér souběžnosti používá nastavení k vyřešení zásobníků volání, které jsou přidruženy k datům o výkonu.  Při procesu trasování, Vizualizér souběžnosti přistupuje k serverům symbolů, které jsou určeny na stránce nastavení.  Při přístupu k těmto datům v síti se zpomaluje zpracování trasování.  Chcete-li zkrátit dobu potřebnou k vyřešení symbolů, můžete symboly uložit do mezipaměti místně. Pokud byly staženy symboly, Visual Studio je načte z místní mezipaměti.

## <a name="just-my-code"></a>Pouze můj kód
 Ve výchozím nastavení je sada pouze můj kód sadou . *exe* a . *DLL* soubory, které jsou přidruženy k aktuálnímu řešení v sadě Visual Studio. Akceměn Vizualizér vyhodnotí tuto sadu souborů při použití pouze můj kód funkce filtrovat zásobníky volání. Na kartě Jen můj kód můžete přidat adresáře, které obsahují . *exe* a . *dll* soubory do umístění, které visualizer souběžnosti používá pro pouze můj kód.

 Cesty . *exe* a . *DLL* soubory jsou uloženy v souboru trasování při shromažďování trasování.  Změna tohoto nastavení nemá vliv na žádné dříve shromážděné trasování.

## <a name="buffering"></a>Vyrovnávací paměti
 Vizualizér souběžnosti používá trasování událostí pro systém Windows (ETW), když shromažďuje trasování.  ETW používá různé vyrovnávací paměti, protože ukládá události.  Výchozí nastavení vyrovnávací paměti ETW nemusí být optimální ve všech případech a v některých případech může způsobit problémy, jako jsou ztracené události.  Kartu Ukládání do vyrovnávací paměti můžete použít ke konfiguraci nastavení vyrovnávací paměti ETW. Další informace naleznete v [tématu Trasování událostí](/windows/win32/etw/event-tracing-portal) a [EVENT_TRACE_PROPERTIES struktura](/windows/win32/api/evntrace/ns-evntrace-event_trace_properties).

## <a name="filter"></a>Filtr
 Na kartě Filtr můžete vybrat sadu událostí, které shromažďuje vizualizér souběžnosti. Výběr podmnožiny událostí omezuje typy dat, které jsou zobrazeny v sestavách, zmenšuje velikost každého trasování a zkracuje čas potřebný ke zpracování trasování.

### <a name="clr-events"></a>CLR – události
 Události generované common language runtime (CLR) umožňují vizualizátoru souběžnosti vyřešit spravované zásobníky volání.  Pokud zakážete shromažďování událostí CLR, bude snížena velikost trasování, ale některé zásobníky volání nebudou vyřešit.  V důsledku toho může být některé aktivity podprocesu procesoru nesprávně kategorizovány.

### <a name="collect-for-native-processes"></a>Sbírat pro nativní procesy
 Ve výchozím nastavení clr události jsou shromažďovány pouze v případě, že je profilován spravovaný proces, protože jsou obvykle zbytečné pro nativní procesy.  V některých případech (například když nativní proces je hostování CLR), bude pravděpodobně muset shromažďovat clr události pro nativní proces.  Pokud se jedná o tento případ, zaškrtněte políčko **Shromáždit pro nativní procesy.**

### <a name="disable-rundown-events"></a>Zakázat rundown ové události
 CLR generuje události ze dvou zprostředkovatelů: runtime a rundown.  Pokud chcete shromažďovat události za běhu CLR, ale chcete se vyhnout shromažďování událostí rundownu, zaškrtněte políčko **Zakázat rundown události.**  Tím se zmenší velikost trasovacího souboru, který je generován kolekce, ale některé zásobníky nemusí vyřešit. Další informace naleznete v tématu [CLR ETW Providers](/dotnet/framework/performance/clr-etw-providers).

### <a name="sample-events"></a>Ukázkové události
 Ukázkové události můžete použít ke shromažďování zásobníků volání, které jsou spojeny s prováděním podprocesu. Tyto události jsou shromažďovány přibližně jednou za milisekundu pro vlákna, která jsou spuštěna v aktuálním procesu. Pokud zakážete kolekci ukázkových událostí, velikost shromážděné trasování je snížena, ale nelze zobrazit žádné zásobníky volání, které jsou spojeny s provádění vlákna.

### <a name="gpu-events"></a>Události GPU
 Události GPU jsou události generované rozhraním DirectX. Pokud zakážete shromažďování událostí GPU, velikost shromážděné trasování se sníží, ale nelze zobrazit žádnou aktivitu GPU v zobrazení využití nebo aktivitu modulu DirectX v zobrazení vláken.

### <a name="file-io-events"></a>Události vstupně-no souborů
 Vstupně-no události souboru představují přístup y k disku jménem aktuálního procesu.  Pokud zakážete události vstupně-videa souboru, velikost trasování se sníží, ale zobrazení vláken nebude hlásit žádné informace o diskových kanálech nebo operacích disku.

## <a name="markers"></a>Značky
 Na **kartě Značky** můžete nakonfigurovat sadu zprostředkovatelů ETW, které jsou zobrazeny jako značky v vizualizéru souběžnosti.  Můžete také filtrovat kolekci Marker na základě úrovně důležitosti a kategorie ETW.  Pokud používáte [souběžnost Vizualizátor SDK](../profiling/concurrency-visualizer-sdk.md) a používáte vlastní zprostředkovatele značky, můžete jej zaregistrovat zde tak, aby se zobrazí v zobrazení vláken.

### <a name="add-a-new-provider"></a>Přidání nového zprostředkovatele
 Pokud váš kód používá [souběžnost Vizualizátor SDK](../profiling/concurrency-visualizer-sdk.md) nebo <xref:System.Diagnostics.Tracing.EventSource> generuje Události ETW, které následují konvence, můžete zobrazit tyto události v akceměn Vizualizátor jejich registrací v tomto dialogovém okně.

 Do pole **Název** zadejte název, který popisuje typy událostí generovaných zprostředkovatelem.  Do pole **GUID** zadejte identifikátor GUID přidružený k tomuto zprostředkovateli. (Identifikátor GUID je přidružen ke každému poskytovateli ETW.)

 Volitelně můžete určit, zda chcete odfiltrovat události od tohoto zprostředkovatele, na základě úrovně kategorie nebo důležitosti.  Pole kategorie můžete použít k filtrování na základě kategorií Vizulizér souběžnosti SDK.  Chcete-li to provést, zadejte řetězec kategorií nebo rozsahů kategorií oddělených čárkami.  Určuje kategorie událostí v aktuálním zprostředkovateli, které chcete zobrazit.  Pokud přidáváte <xref:System.Diagnostics.Tracing.EventSource> zprostředkovatele, můžete použít pole kategorie k filtrování podle klíčového slova ETW.  Vzhledem k tomu, že klíčové slovo je bitová maska, můžete použít řetězec celočísel oddělený čárkami k určení, které bity v masce jsou nastaveny. Například "1,2" nastaví první a druhý bit, což znamená 6 v desítkové.

 Seznam na úrovni důležitosti můžete použít k odfiltrování událostí, které mají důležitost nebo úroveň ETW, která je menší než zadaná hodnota.

### <a name="configure-an-existing-provider"></a>Konfigurace existujícího zprostředkovatele
 Chcete-li upravit nastavení přidružená k existujícímu poskytovateli, vyberte je v seznamu a pak zvolte tlačítko **Upravit zprostředkovatele.**  Můžete změnit nastavení názvu, identifikátoru GUID a filtrování.

### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Filtrování dat značky z přehledů vizualizér souběžnosti
 Pokud nechcete, aby se data pro konkrétního zprostředkovatele zobrazovala v budoucích trasováních, zrušte zaškrtnutí políčka vedle zprostředkovatele, kterého chcete odebrat.

## <a name="files"></a>Soubory
 Na kartě **Soubory** můžete určit adresář, pod kterým jsou soubory trasování uloženy při každém shromažďování trasování.  Vizualizér souběžnosti generuje čtyři soubory pro každé trasování, které shromažďuje:

- Soubor protokolu trasování událostí v režimu jádra (ETL) (<em>.</em> kernel.etl*)

- Soubor protokolu trasování událostí v uživatelském režimu (<em>.</em> user.etl*)

- A Concurrency Visualizer Datový soubor (<em>.</em> CVData*)

- Soubor sledování vizuálu souběžnosti (<em>.</em> CVTrace*)

  Dva soubory ETL ukládat nezpracovaná data trasování a dva concurrency Visualizer soubory uložit zpracovaná data.  Nezpracované soubory ETL se obvykle nepoužívají po zpracování trasování.  Zaškrtnutím políčka **Odstranit protokol etl (Delete Event Trace Log) po analýze** se sníží množství dat trasování, která jsou uložena na disku.

## <a name="see-also"></a>Viz také
- [Jen můj kód](../profiling/just-my-code-threads-view.md)
- [Značky vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md)