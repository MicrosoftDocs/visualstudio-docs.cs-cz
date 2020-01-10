---
title: Dialogové okno Upřesnit nastavení (Vizualizér souběžnosti) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 128327b956734f7d28e7ff88f3eb6c297544587c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849808"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Dialogové okno Upřesnit nastavení (Vizualizér souběžnosti)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí dialogového okna **Upřesnit nastavení** v Vizualizátor souběžnosti můžete řídit, jak se budou shromažďovat trasování.  Dialogové okno obsahuje karty pro symboly, Pouze můj kód, ukládání do vyrovnávací paměti, filtrování, události CLR, značky, zprostředkovatele a soubory.  
  
## <a name="symbols"></a>Symboly  
 Vizualizátor souběžnosti používá stejné nastavení symbolu jako ladicí program sady Visual Studio. Vizualizátor souběžnosti používá nastavení pro řešení zásobníků volání, které jsou spojeny s daty o výkonu.  Při zpracovávání trasování přistupuje Vizualizátor souběžnosti na servery symbolů, které jsou zadány na stránce nastavení.  Když jsou tato data dostupná přes síť, zpracování trasování se zpomaluje.  Chcete-li zkrátit dobu potřebnou k vyřešení symbolů, můžete symboly ukládat místně. Pokud se stáhly symboly, Visual Studio je načte z místní mezipaměti.  
  
## <a name="just-my-code"></a>Pouze můj kód  
 Ve výchozím nastavení je Pouze můj kód sada souborů. exe a. dll, které jsou přidruženy k aktuálnímu řešení v sadě Visual Studio. Vizualizátor souběžnosti vyhodnocuje tuto sadu souborů při použití funkce Pouze můj kód k filtrování zásobníků volání. Na kartě Pouze můj kód můžete přidat adresáře, které obsahují soubory. exe a. dll, do umístění, které používá Vizualizátor souběžnosti pro Pouze můj kód.  
  
 Cesty k souborům. exe a. dll jsou uloženy v trasovacím souboru, když je trasování shromažďováno.  Změna tohoto nastavení neovlivní žádné dříve shromážděné trasování.  
  
## <a name="buffering"></a>Do vyrovnávací paměti  
 Vizualizátor souběžnosti používá trasování událostí pro Windows (ETW) při shromažďování trasování.  ETW používá k ukládání událostí různé vyrovnávací paměti.  Výchozí nastavení vyrovnávací paměti ETW nemusí být optimální ve všech případech a v některých případech může způsobit problémy, jako například ztracené události.  Pomocí karty vyrovnávací paměti můžete nakonfigurovat nastavení vyrovnávací paměti ETW. Další informace najdete v tématu [trasování událostí](https://msdn.microsoft.com/library/bb968803(VS.85).aspx) a [EVENT_TRACE_PROPERTIES struktura](https://msdn.microsoft.com/library/aa363784(VS.85).aspx).  
  
## <a name="filter"></a>Filtrovat  
 Na kartě Filtr můžete vybrat sadu událostí, které shromažďuje Vizualizátor souběžnosti. Výběr podmnožiny událostí omezuje typy dat zobrazených v sestavách, snižuje velikost každého trasování a zkracuje čas potřebný ke zpracování trasování.  
  
### <a name="clr-events"></a>Události CLR  
 Události generované modulem CLR (Common Language Runtime) umožňují Vizualizátor souběžnosti přeložit spravované zásobníky volání.  Pokud zakážete shromažďování událostí CLR, bude snížena velikost trasování, ale některé zásobníky volání nebudou přeloženy.  V důsledku toho může být některá aktivita vlákna procesoru nesprávně zařazená do kategorií.  
  
### <a name="collect-for-native-processes"></a>Shromáždit pro nativní procesy  
 Ve výchozím nastavení jsou události CLR shromažďovány pouze při profilování spravovaného procesu, protože jsou obvykle zbytečné pro nativní procesy.  V některých případech (například pokud je nativní proces hostující modul CLR) může být nutné shromáždit události CLR pro nativní proces.  Pokud se jedná o tento případ, zaškrtněte políčko **shromáždit pro nativní procesy** .  
  
### <a name="disable-rundown-events"></a>Zakázat události doběhu  
 CLR generuje události ze dvou zprostředkovatelů: runtime a doběhu.  Pokud chcete shromažďovat události modulu CLR runtime, ale chcete se vyhnout shromažďování událostí doběhu, zaškrtněte políčko **Zakázat doběhu události** .  Tím se zmenší velikost trasovacího souboru generovaného kolekcí, ale některé zásobníky se nemusí přeložit. Další informace najdete v tématu [Zprostředkovatelé modulu CLR ETW](https://msdn.microsoft.com/library/0beafad4-b2c8-47f4-b342-83411d57a51f) .  
  
### <a name="sample-events"></a>Ukázkové události  
 Můžete použít ukázkové události ke shromáždění zásobníků volání, které jsou spojeny s prováděním vlákna. Tyto události jsou shromažďovány přibližně jednou za milisekundu pro vlákna, která jsou spouštěna v rámci aktuálního procesu. Pokud zakážete shromažďování ukázkových událostí, je velikost shromážděného trasování zmenšena, ale nelze zobrazit žádné zásobníky volání, které jsou spojeny s prováděním vlákna.  
  
### <a name="gpu-events"></a>Události GPU  
 Události GPU jsou události generované rozhraním DirectX. Pokud zakážete shromažďování událostí GPU, velikost shromážděného trasování se zmenší, ale nemůžete zobrazit žádnou aktivitu GPU v zobrazení využití nebo aktivitu modulu DirectX v zobrazení vláken.  
  
### <a name="file-io-events"></a>Vstupně výstupní události souboru  
 Vstupně-výstupní události souboru reprezentují přístup k disku jménem aktuálního procesu.  Pokud zakážete vstupně-výstupní události souboru, bude velikost trasování snížena, ale zobrazení vláken nebude hlásit žádné informace o kanálech disku nebo operacích disku.  
  
## <a name="markers"></a>Značky  
 Na kartě značky můžete nakonfigurovat sadu zprostředkovatelů ETW, které se zobrazí jako značky v Vizualizátor souběžnosti.  Můžete také filtrovat kolekci značek na základě úrovně důležitosti a kategorie ETW.  Pokud používáte [sadu SDK Vizualizátor souběžnosti](../profiling/concurrency-visualizer-sdk.md) a používáte vlastního poskytovatele značek, můžete jej zaregistrovat zde, aby se zobrazil v zobrazení vláken.  
  
### <a name="adding-a-new-provider"></a>Přidává se nový poskytovatel.  
 Pokud váš kód používá [sadu SDK Vizualizátor souběžnosti](../profiling/concurrency-visualizer-sdk.md) nebo GENERUJE události ETW, které následují <xref:System.Diagnostics.Tracing.EventSource> konvence, můžete tyto události zobrazit v Vizualizátor souběžnosti tím, že je zaregistrujete do tohoto dialogového okna.  
  
 Do pole název zadejte název, který popisuje typy událostí, které jsou generovány zprostředkovatelem.  Do pole identifikátor GUID zadejte identifikátor GUID, který je přidružen k tomuto zprostředkovateli. (Identifikátor GUID je spojený s každým poskytovatelem ETW.)  
  
 Volitelně můžete určit, jestli se mají odfiltrovat události od tohoto poskytovatele na základě kategorie nebo úrovně důležitosti.  Pomocí pole kategorie můžete filtrovat podle kategorií Vizualizátor souběžnosti sady SDK.  Provedete to tak, že zadáte řetězec kategorií nebo rozsahy kategorií oddělených čárkami.  Určuje kategorie událostí v aktuálním zprostředkovateli, které se mají zobrazit.  Pokud přidáváte poskytovatele <xref:System.Diagnostics.Tracing.EventSource>, můžete použít pole kategorie k filtrování podle klíčového slova ETW.  Protože klíčové slovo je maskování, můžete použít řetězec celých čísel oddělených čárkami k určení, které bity v masce jsou nastaveny. Například "1, 2" nastaví první a druhý bit a tato možnost se převede na 6 v desítkové soustavě.  
  
 Seznam na úrovni důležitosti můžete použít k vyfiltrování událostí, které mají důležitost nebo úroveň trasování událostí pro Windows, která je menší než zadaná hodnota.  
  
### <a name="configuring-an-existing-provider"></a>Konfigurace existujícího zprostředkovatele  
 Pokud chcete upravit nastavení přidružená k existujícímu zprostředkovateli, vyberte ho v seznamu a pak klikněte na tlačítko **Upravit poskytovatele** .  Můžete změnit název, identifikátor GUID a nastavení filtrování.  
  
### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Filtrovat údaje značek mimo sestavy Vizualizátor souběžnosti  
 Pokud nechcete, aby se data pro konkrétního poskytovatele zobrazovala v budoucích trasováních, zrušte zaškrtnutí políčka u poskytovatele, kterého chcete odebrat.  
  
## <a name="files"></a>Soubory  
 Na kartě **soubory** můžete zadat adresář, ve kterém jsou uloženy trasovací soubory pokaždé, když je trasování shromažďováno.  Vizualizátor souběžnosti generuje čtyři soubory pro každé trasování, které shromažďuje:  
  
- Soubor protokolu trasování událostí v režimu jádra (*. kernel. ETL)  
  
- Soubor protokolu trasování událostí v uživatelském režimu (*. User. ETL)  
  
- Datový soubor Vizualizátor souběžnosti (*. CVData)  
  
- Sledovací soubor Vizualizátor souběžnosti (*. CVTrace  
  
  Tyto dva soubory ETL ukládají nezpracovaná data trasování a dva soubory Vizualizátor souběžnosti ukládají zpracovaná data.  Nezpracované soubory ETL se obvykle nepoužívají po zpracování trasování.  Zaškrtnutím políčka **Odstranit soubory protokolu trasování událostí (ETL) po analýze** dojde k omezení množství dat trasování uložených na disku.  
  
## <a name="see-also"></a>Viz také  
 [Pouze můj kód](../profiling/just-my-code-threads-view.md)   
 [Značky Vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md)
