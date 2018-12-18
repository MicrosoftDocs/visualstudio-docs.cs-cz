---
title: Správa kanálů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89c5727b8bc294ae28f48a6e1fc3194b258b9555
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844423"
---
# <a name="manage-channels"></a>Správa kanálů
V **zobrazení vláken** v vizualizér souběžnosti můžete uspořádat kanály pro proces, takže můžete zkontrolovat určité vzory. Můžete řadit kanály, je přesunout nahoru a dolů a skrytí nebo zobrazení je.  
  
## <a name="sort-by"></a>Řadit podle  
 Můžete ovládacího prvku seřadit podle vláken seřadit podle různých kritérií, podle aktuální úroveň přiblížení. To je obzvláště užitečné, když hledáte konkrétní vzor. Můžete řadit podle těchto kritérií:  
  
|Kritéria|Definice|  
|--------------|----------------|  
|Čas spuštění|Seřadí vláken podle jejich času zahájení. Toto je výchozí pořadí řazení.|  
|Koncový čas|Seřadí vláken podle jejich koncový čas.|  
|Spuštění|Seřadí podle procento času stráveného při provádění vlákna.|  
|Synchronizace|Seřadí vláken podle procento času stráveného v synchronizaci.|  
|I/O|Seřadí vláken podle procento času stráveného v vstupně-výstupní operace (čtení a zápis dat).|  
|Přejít do režimu spánku|Seřadí vláken podle procento času stráveného v režimu spánku.|  
|Stránkování|Seřadí vláken podle procento času stráveného v stránkování.|  
|Přerušování|Seřadí podle procento času stráveného v přerušování vláken.|  
|Zpracování uživatelského rozhraní|Seřadí vláken podle procento času stráveného zpracováním uživatelské rozhraní.|  
  
## <a name="move-selected-channel-up-or-down"></a>Přesunout vybraný kanál nahoru nebo dolů  
 Tyto ovládací prvky můžete přesunout kanál nahoru nebo dolů v seznamu. Například měli byste umístit související kanály vedle sebe můžete zkontrolovat, jestli konkrétní vzor nebo vztah mezi vlákny.  
  
## <a name="move-selected-channel-to-top-or-bottom"></a>Přesunout vybraný kanál horní nebo dolní  
 Přesunutím vybraných kanálů horní nebo dolní části seznamu, abyste mohli prozkoumat konkrétní vzor nebo přesunout některé kanály stranou při kontrole ostatní.  
  
## <a name="hide-selected-channels"></a>Skrýt vybraných kanálů  
 Pokud chcete skrýt kanály, vyberte tento ovládací prvek. Například pokud vlákno synchronizace 100 procent po celou dobu životnosti spravovaného procesu, vám může skrýt jako analyzovat jiná vlákna.  
  
> [!NOTE]
>  Skrytí vlákno také odebere ji z dobu výpočtu, která se zobrazí v legendě aktivní a v sestavách profilu.  
  
## <a name="show-all-channels"></a>Zobrazit všechny kanály  
 Tento ovládací prvek je aktivní, pokud jeden nebo více kanálů jsou skryté. Pokud si zvolíte, se zobrazí všechny elementy skrytá a se vrátíte na výpočty času.  
  
## <a name="move-markers-to-top"></a>Přesunout na začátek značek  
 Obsahuje-li trasování událostí značky, můžete tento příkaz kanály značky přesunout na začátek časovou osu. Jejich relativní pořadí je zachováno.  
  
## <a name="group-markers-by-thread"></a>Skupiny značek vlákno  
 Obsahuje-li trasování událostí značky, můžete tento příkaz kanály značky skupiny v rámci podproces, který vygeneruje události značky.  Kanály disku přesunou do horní části seznamu kanálů a kanály GPU přesunou do dolní.  
  
## <a name="see-also"></a>Viz také:  
 [Ovládací prvek Lupa (zobrazení vláken)](../profiling/zoom-control-threads-view.md)   
 [Režimu míry zapnout nebo vypnout](../profiling/measure-mode-on-off.md)   
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)