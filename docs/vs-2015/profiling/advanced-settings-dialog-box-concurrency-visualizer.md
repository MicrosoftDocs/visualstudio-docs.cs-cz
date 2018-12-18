---
title: Pokročilé dialogové okno nastavení (vizualizér souběžnosti) | Dokumentace Microsoftu
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
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ad91917034dd868aad6c5d78945e4c078fcecee
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749537"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Dialogové okno Upřesnit nastavení (Vizualizér souběžnosti)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S použitím **Upřesnit nastavení** dialogové okno v Concurrency Visualizer můžete řídit, jak se shromáždí trasování.  Dialogové okno obsahuje karty pro symboly, pouze můj kód, ukládání do vyrovnávací paměti, filtrování, CLR události, značky, zprostředkovatele a soubory.  
  
## <a name="symbols"></a>Symboly  
 Vizualizátor souběžnosti používá stejné nastavení symbolu jako ladicí program sady Visual Studio. Vizualizátor souběžnosti používá nastavení pro zásobníky volání, které jsou spojeny s daty výkonu.  Po zpracování trasování, přistupuje k Concurrency Visualizer serverů symbolů, které jsou zadány na stránce nastavení.  Když tato data se přistupuje přes síť, zpracování trasování může zpomalit.  Pokud chcete snížit množství času, které je potřeba vyřešit symboly, můžete ukládat do mezipaměti symbolů místně. Pokud se stáhly symboly, Visual Studio načte z místní mezipaměti.  
  
## <a name="just-my-code"></a>Pouze můj kód  
 Ve výchozím nastavení pouze můj kód je sada souborů .exe a .dll, které jsou spojeny s aktuální řešení v sadě Visual Studio. Vizualizátor souběžnosti vyhodnotí tuto sadu souborů při použití funkce pouze můj kód pro filtrování zásobníky volání. Na kartě funkce pouze můj kód můžete přidat adresáře, které obsahují soubory .exe a .dll do umístění, které používá nástroj Vizualizátor souběžnosti pro volbu pouze vlastní kód.  
  
 Cesty souborů .exe a .dll jsou uloženy v trasovacím souboru při shromážděné trasování.  Změna tohoto nastavení nemá vliv na všechny dříve shromážděná trasování.  
  
## <a name="buffering"></a>ukládání do vyrovnávací paměti  
 Vizualizátor souběžnosti používá trasování událostí pro Windows (ETW), pokud shromáždí trasování.  Trasování událostí pro Windows používá různé vyrovnávací paměti jako ukládá události.  Výchozí nastavení vyrovnávací paměti trasování událostí pro Windows nemusí být optimální ve všech případech a v některých případech, může způsobit problémy, jako jsou ztraceny události.  Karta ukládání do vyrovnávací paměti můžete použít ke konfiguraci nastavení vyrovnávací paměti trasování událostí pro Windows. Další informace najdete v tématu [trasování událostí](http://go.microsoft.com/fwlink/?LinkId=234579) a [EVENT_TRACE_PROPERTIES struktura](http://go.microsoft.com/fwlink/?LinkId=234580).  
  
## <a name="filter"></a>Filtr  
 Na kartě Filtr můžete vybrat sadu událostí, která shromažďuje Vizualizátor souběžnosti. Výběrem podmnožiny události omezuje typy dat, která se zobrazí v sestavách, snižuje velikost každé trasování a zkracuje dobu potřebnou k zpracování trasování.  
  
### <a name="clr-events"></a>Události CLR  
 Události vygenerované Common Language Runtime (CLR) povolte Vizualizátor souběžnosti, chcete-li vyřešit spravované zásobníky volání.  Pokud zakážete shromažďování událostí modulu CLR, bude možné snížit velikost trasování, ale některé zásobníky volání nevyřeší.  V důsledku toho může být nesprávně kategorizovaná nějakou aktivitu vlákna CPU.  
  
### <a name="collect-for-native-processes"></a>Shromáždit pro nativní procesy  
 Ve výchozím nastavení události CLR se shromažďují pouze v případě, že je profilována spravovaného procesu, protože jsou obvykle zbytečné pro nativní procesy.  V některých případech (například když nativní proces je hostitelem modulu CLR) bude pravděpodobně shromažďování událostí modulu CLR pro nativní proces.  Pokud tomu tak, **shromáždit pro nativní procesy** zaškrtávací políčko.  
  
### <a name="disable-rundown-events"></a>Zakázat události Rundown  
 Modul CLR generuje události z dva poskytovatelé: modul runtime a doběhu.  Pokud chcete shromažďování událostí modulu runtime CLR, ale nechcete shromažďování události rundown, vyberte **zakažte události doběhu** zaškrtávací políčko.  To snižuje velikost souboru trasování, který je generován kolekce, ale nemusí vyřešit některé balíčky. Další informace najdete v tématu [CLR ETW – zprostředkovatelé](http://msdn.microsoft.com/library/0beafad4-b2c8-47f4-b342-83411d57a51f)  
  
### <a name="sample-events"></a>Ukázkové události  
 Ukázkové události můžete shromažďovat zásobníky volání, které jsou spojeny s provádění vlákna. Tyto události se shromažďují přibližně jednou za milisekundu pro vlákna, které jsou spuštěny v aktuálním procesu. Pokud zakážete shromažďování události vzorku, zmenšení shromážděného trasování, ale nelze zobrazit žádné zásobníky volání, které jsou spojeny s provádění vlákna.  
  
### <a name="gpu-events"></a>Události GPU  
 Události GPU jsou události generované modulem rozhraní DirectX. Pokud zakážete shromažďování událostí GPU, zmenšení shromážděného trasování, ale nelze zobrazit všechny aktivity GPU v zobrazení využití nebo DirectX modul aktivity v zobrazení vláken.  
  
### <a name="file-io-events"></a>Vstupně výstupní události souboru  
 Soubor vstupně-výstupních operací události představují přístupů na disk jménem aktuální proces.  Pokud zakážete události vstup a výstup souborů, zmenšení trasování, ale zobrazení vláken nebudou oznamovat všechny informace o kanály disku a diskových operací.  
  
## <a name="markers"></a>Značky  
 Na kartě značky můžete nakonfigurovat sady zprostředkovatelů trasování událostí pro Windows, které jsou uvedeny jako značky ve vizualizátoru souběžnosti.  Můžete také filtrovat kolekce značky na základě úroveň důležitosti a kategorie trasování událostí pro Windows.  Pokud používáte [sada Vizualizátor souběžnosti SDK](../profiling/concurrency-visualizer-sdk.md) a použití vlastní poskytovatele značek, můžete ho zaregistrovat tady tak, aby se zobrazí v zobrazení vláken.  
  
### <a name="adding-a-new-provider"></a>Přidání nového poskytovatele  
 Pokud váš kód používá [sada Vizualizátor souběžnosti SDK](../profiling/concurrency-visualizer-sdk.md) nebo generuje události trasování událostí pro Windows, které následují <xref:System.Diagnostics.Tracing.EventSource> konvence, zobrazí se tyto události v Concurrency Visualizer tak, že je zaregistrujete v tomto dialogovém.  
  
 Do pole Název zadejte název, který popisuje typy, které události vygenerované zprostředkovatelem.  Do pole identifikátor GUID zadejte identifikátor GUID, který je spojen s tímto poskytovatelem. (Identifikátor GUID je spojené s každou poskytovatele trasování událostí pro Windows.)  
  
 Volitelně můžete určit, zda chcete vyfiltrovat události z tohoto poskytovatele, podle kategorie nebo důležitost.  Kategorii můžete použít pole, které chcete filtrovat podle kategorií sada Vizualizátor souběžnosti SDK.  Provedete to tak, zadejte řetězec oddělených čárkou kategorií nebo rozsahy kategorií.  Určuje kategorie událostí v rámci aktuálního zprostředkovatele k zobrazení.  Pokud chcete přidat <xref:System.Diagnostics.Tracing.EventSource> poskytovatele, můžete použít pole kategorií můžete filtrovat podle klíčových slov trasování událostí pro Windows.  Protože klíčové slovo je bitová maska, můžete zadat, jsou nastaveny bity, které v masce řetězec celých čísel oddělených čárkou. Například "1,2" Nastaví bity prvního a druhého, a to se přeloží na 6 v desítkové soustavě.  
  
 V seznamu úroveň důležitosti můžete vyfiltrovat události, které mají význam nebo úroveň trasování událostí pro Windows, která je menší než zadanou hodnotou.  
  
### <a name="configuring-an-existing-provider"></a>Konfigurace existujícího poskytovatele  
 Upravit nastavení, které jsou spojeny s existujícího poskytovatele, vyberte ho v seznamu a klikněte na tlačítko **upravit poskytovatele** tlačítko.  Můžete změnit název, identifikátor GUID a filtrování nastavení.  
  
### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Filtrovat značky Data ze sestavy Vizualizéru souběžnosti  
 Pokud nechcete, aby data pro konkrétní zprostředkovatele, aby v budoucnu se zobrazí trasování, zrušte zaškrtnutí políčka u poskytovatele, který chcete odebrat.  
  
## <a name="files"></a>Soubory  
 Na **soubory** kartu, můžete určit adresáře v rámci které trasování jsou soubory uložené trasování pokaždé, když se shromažďují.  Vizualizátor souběžnosti generuje pro každou trasování, které shromažďuje čtyři soubory:  
  
- Soubor protokolu (ETL) jádra události trasování (*. kernel.etl)  
  
- Soubor protokolu trasování událostí uživatelského režimu (*. user.etl)  
  
- Data vizualizátoru souběžnosti soubor (*. CVData)  
  
- Soubor trasování vizualizátoru souběžnosti (*. CVTrace)  
  
  Příslušné dva soubory ETL ukládat data trasování a dva soubory Vizualizátor souběžnosti ukládejte zpracovaná data.  Nezpracovaných souborů ETL se obvykle používá po zpracování trasování.  Výběr **soubory odstranit událost trasování protokolu (ETL) po dokončení analýzy** zaškrtávací políčko snižuje množství dat trasování, která je uložena na disk.  
  
## <a name="see-also"></a>Viz také  
 [Pouze můj kód](../profiling/just-my-code-threads-view.md)   
 [Značky Vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md)



