---
title: Sestava profilu blokování času | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.blocking
helpviewer_keywords:
- Concurrency Visualizer, Blocking Time Profile Report
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3ed24dce0779b9bc7ea9cfd7bedcaa5ca181c68
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926312"
---
# <a name="blocking-time-profile-report"></a>Blokování sestavy časového profilu
Sestavy profilů poskytují agregovaná data o době blokování pro zásobníky volání, které jsou specifické pro každou kategorii blokování (například "V/O" nebo "Synchronizace"). Sestava Preemption uvádí procesy, které předběhly aktuální proces spolu s počtem instancí preemption. Chcete-li vytvořit sestavu blokování profilu, nástroj shromažďuje blokování volání rozhraní API a hromadí je do stromu zásobníků volání. Data zobrazená v těchto sestavách se liší podle aktuálního časového rozsahu, skrytých vláken a následujících dvou filtrů, které mohou být použity:

- Pokud je vybrána možnost Jen můj kód, zobrazí se pouze rámce zásobníku, které mají uživatelský kód, plus jedna úroveň pod uživatelským kódem.

- Pokud je nastavena hodnota snížení šumu, jsou přeskočeny kompletované hromádky, které mají menší než zadaná frekvence.

  Rozbalte libovolnou položku stromu volání a vyhledejte řádek kódu, ve kterém je čas blokování vynakládán. Chcete-li vyhledat řádek zdroje pro položku, zvolte v místní nabídce **možnost Zobrazit zdroj**. Chcete-li vyhledat řádek kódu, který se nazývá tento, zvolte v místní nabídce **možnost Zobrazit weby volání**. Pokud je k dispozici pouze jeden web volání, příkaz se připojí ke zvýrazněnému řádku kódu pro web volání. Pokud je k dispozici více webů volání, příkaz otevře dialogové okno, ve kterém můžete vybrat položku, a pak zvolte tlačítko **Přejít na zdroj,** chcete-li vyhledat zvýrazněný web volání. Často je nejužitečnější zobrazit zdrojový kód pro web volání, který má nejvíce instancí, nejvíce času nebo obojí.

## <a name="blocking-time-report-columns"></a>Blokování sloupců časové sestavy
 V následující tabulce jsou uvedeny sloupce pro každou sestavu času blokování.

|Název sloupce|Popis|
|-----------------|-----------------|
|**Název**|Název funkce pro každou úroveň zásobníku volání.|
|**Instance**|Počet instancí blokování volání viditelné časové období.|
|**Včetně doba blokování**|Celková doba blokování, která je vynaložena pro všechny zásobníky, které se shrnou na tuto úroveň stromu zásobníku volání. Včetně číslo je součet výhradní blokování čas pro tuto funkci a výhradní blokování čas pro všechny jeho podřízené uzly.|
|**Exkluzivní doba blokování**|Celková doba blokování, která je strávená během této funkce je nejnižší úroveň zásobníku volání. Jedinečná položka zásobníku volání, která má vysokou výhradní blokování čas může být funkce zájmu.|
|**Kategorie API/Čekání**|Zobrazuje se pouze pro funkce na nejnižší úrovni zásobníku volání. Pokud je rozpoznán podpis blokování volání, je k dispozici název blokování rozhraní API. Pokud podpis není rozpoznán, jsou k dispozici informace, které jsou hlášeny jádrem.|
|**Podrobnosti**|Plně kvalifikovaný název funkce. To zahrnuje počet řádků, když je k dispozici.|

### <a name="synchronization"></a>Synchronizace
 Sestava synchronizace zobrazuje volání, které jsou zodpovědné za segmenty, které blokují synchronizaci, a agregační doby blokování každého zásobníku volání. Další informace naleznete v [tématu Doba synchronizace](../profiling/synchronization-time.md).

### <a name="sleep"></a>Režim spánku
 Sestava spánku zobrazuje volání, které jsou zodpovědné za blokování času, který byl přiřazen k času strávenému spánku a agregační blokování časy každého zásobníku volání. Další informace naleznete v [tématu Doba spánku](../profiling/sleep-time.md).

### <a name="io"></a>I/O
 Vstupně-v., zobrazuje volání, které jsou zodpovědné za segmenty, které blokují vstupně-va a a souhrnné blokování časy každého zásobníku volání. Další informace naleznete [v tématu V/V čas (zobrazení vláken)](../profiling/i-o-time-threads-view.md).

### <a name="memory-management"></a>Správa paměti
 Sestava správy paměti zobrazuje volání, které jsou zodpovědné za segmenty, které blokují operace správy paměti, a agregační doby blokování každého zásobníku volání. Další informace naleznete v [tématu Memory management time](../profiling/memory-management-time.md).

### <a name="preemption"></a>Prevence
 Sestava Preemption uvádí procesy, které předběhly aktuální proces spolu s počtem instancí.  Každý proces můžete rozbalit a zobrazit konkrétní vlákna, která nahradila vlákna v aktuálním procesu, a zobrazit rozdělení instancí preemption na vlákno. Tato blokovací sestava je méně žalovatelná než ostatní, protože předkupní právo je obvykle uloženo na váš proces operačním systémem, nikoli problémem v kódu. Další informace naleznete v tématu [Preemption time](../profiling/preemption-time.md).

### <a name="ui-processing"></a>Zpracování ui
 Sestava zpracování ui zobrazuje volání, které jsou zodpovědné za blokování segmentů, které blokují na bloky zpracování ui a agregační blokování časy každého zásobníku volání. Další informace naleznete [v tématu doba zpracování ui](../profiling/ui-processing-time.md).

## <a name="see-also"></a>Viz také
- [zobrazení vláken](../profiling/threads-view-parallel-performance.md)