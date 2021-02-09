---
title: Správa kanálů | Microsoft Docs
description: Přečtěte si, jak můžete organizovat kanály pro svůj proces, abyste mohli kontrolovat konkrétní vzory v zobrazení vláken v Vizualizátor souběžnosti.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ebeb885d427cf6a9a6ca80d4d0ad572b23d7f685
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917790"
---
# <a name="manage-channels"></a>Správa kanálů
V **zobrazení vláken** v Vizualizátor souběžnosti můžete uspořádat kanály pro svůj proces, abyste mohli kontrolovat konkrétní vzory. Kanály můžete seřadit, přesunout je nahoru a dolů a skrýt nebo zobrazit.

## <a name="sort-by"></a>Řadit podle
 Pomocí ovládacího prvku seřadit podle můžete řadit vlákna podle různých kritérií, a to na základě aktuální úrovně přiblížení. To je užitečné hlavně v případě, že hledáte konkrétní vzor. Můžete řadit podle těchto kritérií:

|Kritéria|Definice|
|--------------|----------------|
|Čas spuštění|Seřadí vlákna podle jejich počátečních časů. Toto je výchozí pořadí řazení.|
|Čas ukončení|Seřadí vlákna podle jejich koncových časů.|
|Spuštění|Seřadí vlákna podle procenta času stráveného při provádění.|
|Synchronizace|Seřadí vlákna podle procenta času stráveného při synchronizaci.|
|I/O|Seřadí vlákna podle procenta času stráveného při vstupně-výstupních operacích (čtení a zápis dat).|
|Režim spánku|Seřadí vlákna podle procenta času stráveného v režimu spánku.|
|Stránkování|Seřadí vlákna podle procenta času stráveného na stránkování.|
|Přerušení|Seřadí vlákna podle procenta času stráveného při přerušení.|
|Zpracování uživatelského rozhraní|Seřadí vlákna podle procenta času stráveného při zpracování uživatelského rozhraní.|

## <a name="move-selected-channel-up-or-down"></a>Přesunout vybraný kanál nahoru nebo dolů
 Pomocí těchto ovládacích prvků můžete v seznamu přesunout kanál nahoru nebo dolů. Můžete například umístit související kanály vedle sebe, které vám pomohou kontrolovat konkrétní vzor nebo vztah mezi vlákny.

## <a name="move-selected-channel-to-top-or-bottom"></a>Přesunout vybraný kanál na horní nebo dolní
 Vybrané kanály můžete přesunout do horní nebo dolní části seznamu, abyste mohli kontrolovat konkrétní vzor nebo přesouvat některé kanály při prozkoumávání ostatních.

## <a name="hide-selected-channels"></a>Skrýt vybrané kanály
 Tento ovládací prvek vyberte, pokud chcete skrýt kanály. Například pokud je vlákno 100% synchronizace po dobu životnosti spravovaného procesu, můžete ho skrýt při analýze jiných vláken.

> [!NOTE]
> Skrytím vlákna také odeberete z času výpočtu, který je zobrazen v aktivní legendě a v sestavách profilu.

## <a name="show-all-channels"></a>Zobrazit všechny kanály
 Tento ovládací prvek je aktivní, když je jeden nebo více kanálů skrytý. Pokud zvolíte tuto možnost, zobrazí se všechny skryté prvky a vrátí se do výpočtů času.

## <a name="move-markers-to-top"></a>Přesunout značky na začátek
 Pokud trasování obsahuje události značek, můžete pomocí tohoto příkazu Přesunout kanály značek do horní části časové osy. Jejich relativní pořadí se zachová.

## <a name="group-markers-by-thread"></a>Seskupit značky podle vlákna
 Pokud trasování obsahuje události značek, můžete použít tento příkaz k seskupení kanálů značek ve vlákně, které vygenerovalo události značky.  Kanály disku se přesunou na začátek seznamu kanálů a kanály GPU se přesunou do dolní části.

## <a name="see-also"></a>Viz také
- [Ovládací prvek Lupa (zobrazení vláken)](../profiling/zoom-control-threads-view.md)
- [Zapnout nebo vypnout režim míry](../profiling/measure-mode-on-off.md)
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)