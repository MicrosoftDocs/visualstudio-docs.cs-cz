---
title: Blokování času Sestava profilu | Dokumentace Microsoftu
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
- vs.cv.threads.report.blocking
helpviewer_keywords:
- Concurrency Visualizer, Blocking Time Profile Report
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31be25e5fb41f2e7a92ee2c19803d74c442fcad4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807020"
---
# <a name="blocking-time-profile-report"></a>Sestava profilu času blokace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil sestavy poskytují data agregace času blokování pro zásobníky volání, které jsou specifické pro každou blokování kategorii (například "Vstupně-výstupní operace" nebo "Synchronizace"). Přerušení sestava obsahuje seznam procesů, které ke zrušení přidělením aktuální proces a počtem instancí přerušení. Pokud chcete sestavit blokování Sestava profilu, nástroj shromáždí blokování volání rozhraní API a shromáždí do stromu zásobníky volání. Data zobrazená v těchto sestavách se liší podle aktuální časový rozsah, skryté vláken a následující dva filtry, které mohou být použity:  
  
- Pokud je vybrána pouze můj kód, jsou uvedeny pouze bloky zásobníku, které mají kód uživatele a jednu úroveň níže uvedeného kódu uživatele.  
  
- Pokud je nastavena hodnota snížení šumu, porovnávány zásobníky, kterých je nižší než zadané frekvence se přeskočí.  
  
  Rozbalte všechny položky strom volání najít řádek kódu, ve kterém byl stráven času blokování. Vyhledejte řádek zdroje pro položku, na místní nabídku, vyberte **zobrazit zdroj**. Chcete-li vyhledejte řádek kódu, který volal to předchozí, v místní nabídce zvolte **lokalit volání zobrazení**. Pokud pouze jedna lokalita volání je k dispozici, příkaz se připojí k zvýrazněný řádek kódu pro web volání. Pokud jsou k dispozici více lokalit volání, příkaz se otevře dialogové okno, ve kterém můžete vybrat položku a klikněte na tlačítko **přejít ke zdroji** vyhledejte zvýrazněné volání webu. Často je nejužitečnější, chcete-li zobrazit zdrojový kód pro lokalitu volání, která má nejvíce instance nebo nejvíce času.  
  
## <a name="blocking-time-report-columns"></a>Blokování času sloupce sestavy  
 V následující tabulce jsou uvedeny sloupce pro každou sestavu blokování času.  
  
|Název sloupce|Popis|  
|-----------------|-----------------|  
|Název|Název funkce pro každou úroveň zásobníku volání.|  
|Instance|Počet instancí blokovacího hovoru viditelném časovém období.|  
|Celkový čas blokace|Celkový počet blokování času stráveného pro všechny balíčky, které jsou zahrnuty do této úrovně stromu zásobníku volání. Celkový počet je součtem výhradní čas zablokování pro tuto funkci a výhradní čas zablokování pro všechny jeho podřízené uzly.|  
|Výhradní čas blokace|Celková doba blokování, který byl stráven během které bude tato funkce je nejnižší úroveň zásobníku volání. Položka zásobníku volání jedinečné, který má vysokou výhradní čas zablokování může být funkce, které vás zajímají.|  
|Kategorie API/Wait|Platné pouze pro funkce na nejnižší úrovni zásobníku volání. Pokud je rozpoznána podpis blokovacího hovoru, je zadaný název blokování rozhraní API. Pokud podpis nebyl rozpoznán, je k dispozici informace, která je ohlášena jádra.|  
|Podrobnosti|Plně kvalifikovaný název funkce. To zahrnuje počet řádků, až bude k dispozici.|  
  
### <a name="synchronization"></a>Synchronizace  
 Synchronizace sestava ukazuje volání, které jsou zodpovědné za segmenty, které blokují na synchronizaci a agregace blokování časy každý zásobník volání. Další informace najdete v tématu [čas synchronizace](../profiling/synchronization-time.md)  
  
### <a name="sleep"></a>Přejít do režimu spánku  
 Sestava režimu spánku zobrazí volání, které jsou zodpovědné za čas, který byl přiřadit čas, který byl stráven v režimu spánku, agregační blokování časy každý zásobník volání a blokuje. Další informace najdete v tématu [přejít do režimu spánku čas](../profiling/sleep-time.md).  
  
### <a name="io"></a>I/O  
 Vstupně-výstupních operací sestava ukazuje volání, které jsou zodpovědné za segmenty, které blokují na vstupně-výstupní operace a agregace blokování časy každý zásobník volání. Další informace najdete v tématu [čas I/O (zobrazení vláken)](../profiling/i-o-time-threads-view.md).  
  
### <a name="memory-management"></a>Správa paměti  
 Správa paměti sestava ukazuje volání, které jsou zodpovědné za segmenty, které blokují na agregaci blokování časy jednotlivých volání zásobníků a operace správy paměti. Další informace najdete v tématu [čas správy paměti](../profiling/memory-management-time.md).  
  
### <a name="preemption"></a>Přerušení  
 Sestava přerušení vypíše procesy, které ke zrušení přidělením aktuální proces a počtem instancí.  Můžete rozbalit každý proces chcete zobrazit konkrétní vláken, která nahradí vlákna v aktuálním procesu a chcete-li zobrazit rozpis instancí přerušení na vlákno. Tato blokující zpráva je méně užitečné než ostatní, protože přerušení je obvykle uložené v procesu operačního systému, nikoli k problému v kódu. Další informace najdete v tématu [čas přerušení](../profiling/preemption-time.md).  
  
### <a name="ui-processing"></a>Zpracování uživatelského rozhraní  
 Sestava zpracování uživatelského rozhraní obsahuje volání, které jsou zodpovědné za blokování segmenty, které blokují na bloky zpracování uživatelského rozhraní a agregace blokování časy každý zásobník volání. Další informace najdete v tématu [doba zpracování uživatelského rozhraní](../profiling/ui-processing-time.md).  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)



