---
title: Přehled sestav výkonu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 455c05ae0d8645040d3f9eac68d20f57138df5cb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830766"
---
# <a name="performance-report-overview"></a>Sestava Přehled výkonu
Můžete zobrazit data profilování relace výkonu v **sestavu výkonu** okno integrovaného vývojového prostředí (IDE) Visual Studio Team System Development Edition. Data profilace se uloží do souborů .vsp a .vsps. Zobrazení sestav systému windows umožňují zobrazit a analyzovat problémy s výkonem aplikací.  
  
> [!CAUTION]
>  Soubor dat profilování obsahuje citlivé informace, jako je název počítače, na verzi operačního systému, cesty k souborům, informace o paměti a další informace o nastavení počítače. By měl zachovat přísnou kontrolu distribuce dat, jak v jeho nativní. *vsp* formátu a při exportu do. *CSV* nebo. *XML* souboru.  
>   
>  Je-li jako část relace výkonu se shromažďují data trasování událostí, další informace může zobrazit událostí protokolu trasování (. *ETL*) souboru. Tyto informace zahrnují své domény a uživatelské jméno; Proto je vhodné ponechat striktní kontrolu nad rozdělení souboru protokolu.  
  
## <a name="performance-report-window"></a>Okno Sestava výkonu  
 Sestava výkonu okno je okno nástroje, který se používá k zobrazení, spravovat a filtrovat data o výkonu a obsahuje ovládací prvek přizpůsobitelné dotazu.  
  
 Na hlavním panelu nástrojů okna sestavy výkonu můžete zobrazit každý. Klikněte na šipku vedle položky **aktuální zobrazení** seznamu k zobrazení a vyberte jednotlivé zobrazení, které jsou k dispozici.  
  
 V okně sestavy výkonu najdete následující zobrazení, data:  
  
### <a name="summary-view"></a>Souhrnné zobrazení  
 Ve výchozím nastavení se data profilování zobrazí v souhrnném zobrazení. Toto zobrazení je výchozím bodem při šetření do problémy s výkonem. Z každého řádku v souhrnném zobrazení můžete přesunout na podrobnější zobrazení kliknutím pravým tlačítkem myši název funkce nebo modulu. Další informace najdete v tématu [souhrnné zobrazení](../profiling/summary-view.md).  
  
### <a name="callercallee-view"></a>Zobrazení volající/volaný  
 Volající/volaný – zobrazení stromu volání pro jednotlivé funkce. Zobrazení je rozdělené do tří částí:  
  
- Cílová funkce se zobrazí uprostřed zobrazení.  
  
- Funkce, které volal funkci (volající) se zobrazí nad cílová funkce.  
  
- Funkce, které jsou volány cílová funkce (volané) se zobrazí pod cíl.  
  
  Dvojitým kliknutím na libovolnou funkci v volané seznamu nebo volaný můžete vybrat jiné funkce. Další informace najdete v tématu [zobrazení volající/volaný](../profiling/caller-callee-view.md).  
  
### <a name="call-tree-view"></a>Zobrazení stromu volání  
 Zobrazení stromu volání zobrazí cesty spuštění funkce, které byly Procházet v profilované aplikaci. Kořen stromu je vstupním bodem do aplikace nebo komponenty. Každý uzel funkce obsahuje všechny funkce, které ji volaly a údaje o výkonu o volání těchto funkcí.  
  
 Zobrazení stromu volání můžete také rozšířit a zvýrazňovat cesta provedení funkce, která nejvíce času spotřebovaného nebo vzorkováno nejčastěji. Zobrazit Nejaktivnější cestu, klikněte pravým tlačítkem na funkci a pak klikněte na **rozbalit kritickou cestu**. Další informace najdete v tématu [zobrazení stromu volání](../profiling/call-tree-view.md).  
  
### <a name="process-view"></a>Zobrazení procesů  
 Proces zobrazení ukazuje údaje o výkonu pro každý proces a vlákna, která je profilována. Další informace najdete v tématu [zobrazení procesu](../profiling/process-view.md).  
  
### <a name="modules-view"></a>Zobrazení modulů  
 Zobrazení modulů seznam modulů v projektu a prezentuje profilovacích dat pro každý modul. Rozbalit nebo sbalit název modulu pro zobrazení funkce data profilace. Když byly údaje shromážděny pomocí vzorkování, zdrojový kód řádku a instrukce ukazatel myši data profilace je také k dispozici. Další informace najdete v tématu [moduly zobrazení](../profiling/modules-view.md).  
  
### <a name="functions-view"></a>Zobrazení funkcí  
 Zobrazení funkcí jsou uvedeny funkce, které byly volány během profilace. Další informace najdete v tématu [zobrazení funkcí](../profiling/functions-view.md).  
  
### <a name="line-view"></a>Řádky – zobrazení  
 Zobrazení řádků umožňuje zobrazit konkrétnímu zdroji řádků kódu, které byly provedeny během profilace vzorkování. Další informace najdete v tématu [zobrazení řádků](../profiling/lines-view.md).  
  
### <a name="instruction-pointer-ip-view"></a>Zobrazení ukazatele (IP adresa) instrukce  
 Zobrazení ukazatele na instrukci umožňuje zobrazit konkrétní pokyny, které byly spuštěny během profilace vzorkování. Další informace najdete v tématu [zobrazení ukazatele na instrukce (IP)](../profiling/instruction-pointers-ips-view.md).  
  
### <a name="allocation-view"></a>Zobrazení přidělení  
 Zobrazení přidělení je k dispozici Pokud **přidělování objektů .NET shromažďovat** byla vybrána na **Obecné** stránku **relace výkonu** dialogové okno Vlastnosti. Viz [Přehled relace výkonu](../profiling/performance-session-overview.md). Zobrazení přidělení seznam objektů .NET, které byly přiděleny aplikace nebo součásti. Při rozbalení řádku objektu, zobrazí se strom volání. Strom volání ukazuje cesty spuštění, z kterých vzniklo při vytvoření objektu. Zobrazí informace o počtu zahrnuté a výhradní přidělení pro každou funkci ve stromu volání se také. Zobrazení přidělení můžete také rozšířit a zvýrazňovat cesta provedení funkce, která přidělené nejvyšší počet objektů. Zobrazit Nejaktivnější cestu, klikněte pravým tlačítkem na funkci a pak klikněte na **rozbalit kritickou cestu**. Další informace naleznete v tématu [.NET shromažďovat data přidělení a životnost paměti](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) a [zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md).  
  
### <a name="objects-lifetime-view"></a>Zobrazení doby života objektů  
 Zobrazení doby života objektu je k dispozici Pokud **.NET shromažďovat informace o přidělení objektu** a **také shromažďovat informace o životnosti objektů .NET** byly vybrány v **Obecné**stránku **relace výkonu** dialogové okno Vlastnosti.  
  
 Doba života objektu zobrazí celkový počet instancí každého typu a počtu objektů, které byly shromážděny v každé generaci uvolňování paměti. Další informace najdete v tématu [zobrazení doby života objektu](../profiling/object-lifetime-view.md).  
  
## <a name="customizable-filter-control"></a>Ovládací prvek filtru lze přizpůsobit  
 Ovládací prvek přizpůsobitelné filtru obsahuje následující možnosti:  
  
-   **Filtr pro import** -načte dříve uložený vlastní dotaz.  
  
-   **Exportovat filtr** – uloží vlastní dotaz do zadaného umístění.  
  
-   **Spuštění dotazu** – spustí dotaz, jak se zobrazuje v ovládacím prvku vlastní dotaz.  
  
-   **Zastavit dotaz** -zastaví provádění dotazu, který je spuštěn. Toto tlačítko není k dispozici, pokud je spuštěn žádný dotaz.  
  
-   **Zobrazit dotaz** – zobrazí nebo skryje ovládacího prvku vlastní dotaz.  
  
-   **Uložit Analyzed** – uloží zprávu společně s jeho aktuální analýzy jako soubor .vsps.  
  
-   **Export** – uloží aktuální sestavu v. Ve formátu CSV nebo. XML soubor ve formátu, s možnostmi pro uložení různých zobrazení.  
  
## <a name="see-also"></a>Viz také:  
 [Analýza dat nástrojů pro výkon](../profiling/analyzing-performance-tools-data.md)   
 [Zobrazení sestav výkonu](../profiling/performance-report-views.md)