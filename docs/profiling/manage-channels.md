---
title: Správa kanálů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1480bab2f52383a8ca3a5b0ac22fd56acb5e01
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "64779252"
---
# <a name="manage-channels"></a>Správa kanálů
V **zobrazení vláken** v vizualizéru souběžnosti můžete uspořádat kanály pro váš proces tak, aby bylo možné prozkoumat konkrétní vzory. Kanály můžete řadit, přesouvat nahoru a dolů a skrývat nebo zobrazovat.

## <a name="sort-by"></a>Řadit podle
 Ovládací prvek Seřadit podle můžete použít k seřazení vláken podle různých kritérií na základě aktuální úrovně přiblížení. To je užitečné zejména při hledání určitého vzoru. Můžete řadit podle těchto kritérií:

|Kritéria|Definice|
|--------------|----------------|
|Čas spuštění|Seřadí vlákna podle počátečních časů. Toto je výchozí pořadí řazení.|
|Čas ukončení|Seřadí vlákna podle jejich koncových časů.|
|Spouštěcí|Seřadí vlákna podle procenta času stráveného v provádění.|
|Synchronizace|Seřadí vlákna podle procenta času stráveného synchronizací.|
|I/O|Seřadí vlákna podle procenta času stráveného v stupněm vstupně-up (čtení a zápis dat).|
|Režim spánku|Seřadí vlákna podle procenta času stráveného ve spánku.|
|Stránkování|Seřadí vlákna podle procenta času stráveného stránkováním.|
|Prevence|Seřadí vlákna podle procenta času stráveného v preemption.|
|Zpracování ui|Seřadí vlákna podle procenta času stráveného při zpracování uživatelského rozhraní.|

## <a name="move-selected-channel-up-or-down"></a>Přesunutí vybraného kanálu nahoru nebo dolů
 Pomocí těchto ovládacích prvků můžete v seznamu přesunout kanál nahoru nebo dolů. Můžete například umístit související kanály vedle sebe, abyste mohli prozkoumat určitý vzorek nebo vztah mezi vlákny.

## <a name="move-selected-channel-to-top-or-bottom"></a>Přesunutí vybraného kanálu na začátek nebo dolů
 Vybrané kanály můžete přesunout do horní nebo dolní části seznamu, abyste mohli prozkoumat určitý vzorek, nebo přesunout některé kanály z cesty, když zkoumáte ostatní.

## <a name="hide-selected-channels"></a>Skrytí vybraných kanálů
 Tento ovládací prvek zvolte, pokud chcete kanály skrýt. Například pokud vlákno je 100 procent synchronizace po dobu životnosti spravovaného procesu, můžete skrýt při analýze jiných vláken.

> [!NOTE]
> Skrytím vlákna se také odebere z doby výpočtu, která je zobrazena v aktivní legendě a v přehledech profilů.

## <a name="show-all-channels"></a>Zobrazit všechny kanály
 Tento ovládací prvek je aktivní, pokud je jeden nebo více kanálů skrytých. Pokud ji zvolíte, zobrazí se všechny skryté prvky a vrátí se do výpočtů času.

## <a name="move-markers-to-top"></a>Přesunutí značek nahoru
 Pokud trasování obsahuje události značky, můžete pomocí tohoto příkazu přesunout kanály značek na začátek časové osy. Jejich relativní řád je zachován.

## <a name="group-markers-by-thread"></a>Seskupit značky podle nitě
 Pokud trasování obsahuje události značky, můžete pomocí tohoto příkazu seskupit kanály značek pod vláknem, které vygenerovalo události značky.  Diskové kanály jsou přesunuty do horní části seznamu kanálů a gpu kanály jsou přesunuty na konec.

## <a name="see-also"></a>Viz také
- [Ovládání lupy (zobrazení vláken)](../profiling/zoom-control-threads-view.md)
- [Zapisování/vypínání režimu měření](../profiling/measure-mode-on-off.md)
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)