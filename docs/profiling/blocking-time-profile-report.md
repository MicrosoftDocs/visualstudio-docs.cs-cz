---
title: Sestava profilu času blokování | Microsoft Docs
description: 'Sestavy profilu času blokace poskytují agregovaná data o době blokování. K dispozici je šest typů sestav: synchronizace, režim spánku, vstupně-výstupní operace, paměť, přerušení a uživatelské rozhraní.'
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 74cfeb0b93b1819b4491b18b8e455b3c8d49be4d
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204576"
---
# <a name="blocking-time-profile-report"></a>Sestava profil času blokování
Sestavy profilu poskytují agregovaná data o době blokování pro zásobníky volání, která jsou specifická pro jednotlivé kategorie blokování (například I/O nebo synchronizace). Sestava přerušení obsahuje seznam procesů, které přecházely aktuální proces spolu s počtem instancí přerušení. Chcete-li vytvořit sestavu blokující profil, nástroj shromáždí blokování volání rozhraní API a shromáždí je do stromu zásobníků volání. Data zobrazená v těchto sestavách se liší podle aktuálního časového rozsahu, skrytého vlákna a pomocí následujících dvou filtrů, které mohou být aplikovány:

- Pokud je vybráno Pouze můj kód, zobrazí se pouze rámce zásobníku s uživatelským kódem a jedna úroveň pod uživatelským kódem.

- Pokud je nastavená hodnota snížení šumu, přeskočí se zásobníky, které mají míň, než je zadaná frekvence.

  Rozbalením položky stromu volání vyhledejte řádek kódu, ve kterém je čas blokace stráven. Chcete-li vyhledat řádek zdroje pro položku, v místní nabídce vyberte možnost **Zobrazit zdroj**. Chcete-li najít řádek kódu, který se nazývá tento kód, v místní nabídce vyberte možnost **Zobrazit weby volání**. Pokud je k dispozici pouze jedna lokalita volání, příkaz se připojí k zvýrazněnému řádku kódu pro volání webu. Je-li k dispozici více webů volání, příkaz otevře dialogové okno, ve kterém můžete vybrat položku a pak kliknutím na tlačítko **Přejít do zdroje** vyhledat zvýrazněný web volání. Je často vhodné zobrazit zdrojový kód pro web volání, který má nejvíce instancí, nejvíce času nebo obojího.

## <a name="blocking-time-report-columns"></a>Sloupce sestavy doby blokování
 V následující tabulce jsou uvedeny sloupce pro každou sestavu doby blokování.

|Název sloupce|Popis|
|-----------------|-----------------|
|**Název**|Název funkce pro každou úroveň zásobníku volání.|
|**Instance**|Počet instancí blokujícího volání pro zobrazené časové období.|
|**Celková doba blokování**|Celkový čas blokování strávený pro všechny zásobníky, které jsou zahrnuty na tuto úroveň stromu zásobníku volání. Celkové číslo (včetně) je součet exkluzivní doby blokování pro tuto funkci a výhradním časem blokování pro všechny jeho podřízené uzly.|
|**Výhradní čas blokace**|Celkový čas blokace, který strávil, že tato funkce je nejnižší úroveň zásobníku volání. Jedinečná položka zásobníku volání, která má vysokou výhradní dobu blokování, může být funkce, kterou je třeba zajímat.|
|**Kategorie API/Wait**|Zobrazuje se pouze pro funkce na nejnižší úrovni zásobníku volání. Kde je rozpoznán podpis blokujícího volání, je k dispozici název blokujícího rozhraní API. Pokud signatura není rozpoznaná, poskytnou se informace hlášené jádrem.|
|**Podrobnosti**|Plně kvalifikovaný název funkce. To zahrnuje počet řádků, je-li k dispozici.|

### <a name="synchronization"></a>Synchronizace
 Sestava synchronizace zobrazuje volání, která jsou zodpovědná za segmenty blokující synchronizaci, a agregované doby blokování jednotlivých zásobníků volání. Další informace najdete v tématu [čas synchronizace](../profiling/synchronization-time.md).

### <a name="sleep"></a>Režim spánku
 Sestava spánku zobrazuje volání, která jsou zodpovědná za blokování času, který byl vytvořen jako čas strávený v režimu spánku, a agregované doby blokování jednotlivých zásobníků volání. Další informace najdete v tématu [Doba spánku](../profiling/sleep-time.md).

### <a name="io"></a>I/O
 Sestava v/v zobrazuje volání, která jsou zodpovědná za segmenty blokující při vstupně-výstupních operacích, a agregované doby blokování jednotlivých zásobníků volání. Další informace naleznete v části [vstupně-výstupní čas (zobrazení vláken)](../profiling/i-o-time-threads-view.md).

### <a name="memory-management"></a>Správa paměti
 Sestava správy paměti zobrazuje volání, která jsou zodpovědná za segmenty blokující operacemi správy paměti, a agregované doby blokování jednotlivých zásobníků volání. Další informace najdete v tématu [čas správy paměti](../profiling/memory-management-time.md).

### <a name="preemption"></a>Přerušení
 Sestava přerušení obsahuje seznam procesů, které procházely aktuálnímu procesu spolu s počtem instancí.  Jednotlivé procesy můžete rozbalit, chcete-li zobrazit konkrétní vlákna, která nahradila vlákna v aktuálním procesu a zobrazit rozpis instancí přerušení na vlákno. Tato blokující sestava je méně napadnutelná než u ostatních, protože je obvykle ukládána do procesu operačním systémem, nikoli při potížích ve vašem kódu. Další informace najdete v tématu [čas přerušení](../profiling/preemption-time.md).

### <a name="ui-processing"></a>Zpracování uživatelského rozhraní
 Sestava zpracování uživatelského rozhraní zobrazuje volání, která jsou zodpovědná za blokování segmentů, které jsou blokovány při zpracování bloků uživatelského rozhraní, a agregovaná doba blokace každého zásobníku volání. Další informace najdete v tématu [Doba zpracování uživatelského rozhraní](../profiling/ui-processing-time.md).

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)