---
title: Legenda zobrazení jader | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ea3184fbcd3561b88521f7dbdf4bf44c925150d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62553160"
---
# <a name="cores-view-legend"></a>Legenda zobrazení jader
Legenda zobrazení jader identifikuje každé vlákno podle barvy a názvu. Obsahuje sloupce, které zobrazují počty pro přepnutí kontextu mezi jádry, celkové přepnutí kontextu a procento přepínačů kontextu, které se protínají jádry. Řádky v legendě jsou seřazeny podle počtu přepínačů kontextu mezi jádry v sestupném pořadí.

 Můžete vybrat řádky v legendě a filtrovat vlákna, která jsou zobrazena na časové ose. Na časové ose jsou zobrazena pouze vybraná vlákna. Pokud nejsou vybrány žádné řádky, zobrazí se všechny řádky na časové ose.

 Přepnutí kontextu mezi jádry stojí více režie a výkonu než přepínače, které zůstávají na stejném logickém jádru. Během přepnutí kontextu jsou registry procesoru uloženy a obnoveny, spustí se kód jádra operačního systému, znovu se načíst položky vyrovnávací paměti lookaside překladu a vyprázdní se kanál procesoru. Přepnutí kontextu mezi jádry může být ještě dražší než jiné přepnutí kontextu, protože data mezipaměti nejsou platná pro toto vlákno v jiném jádru. Naproti tomu pokud je vlákno přepnuto do jádra, na které bylo dříve spuštěno, je pravděpodobné, že užitečná data jsou stále v mezipaměti. Pokud byly přepínače kontextu mezi jádry zvýšeny pokusy o správu spřažení vláken a snížení výkonu, zvažte, zda tento problém vyřešit. Začněte odstraněním spřažení vláken a pak sledujte výsledné chování mezi jádry.

 Následující tabulka popisuje prvky legendy.

|Element|Definice|
|-------------|----------------|
|Název vlákna|Zobrazuje barvu vlákna v časové ose předchozích jader a název tohoto vlákna.|
|Přepnutí kontextu mezi jádry|Počet přepnutí kontextu pro vlákno, které také přešel z jednoho logického jádra do druhého. Nerozlišuje mezi mezi-core kontextové přepínače, které kříž z jednoho procesoru zemřít na jiný oproti těm, které zůstávají na stejné die.|
|Celkový počet přepnutí kontextu|Celkový počet přepnutí kontextu pro dané vlákno během období vzorkování. Pokaždé, když vlákno změní kontext (například od spuštění k synchronizaci) se počítá jeden přepínač kontextu.|
|Procento přepnutí kontextu, které křížová jádra|Vypočítá se v procentech vydělením počtu přepnutí kontextu mezi jádry počtem celkových přepnutí kontextu. Čím vyšší je toto procento, tím větší je celkový účinek režie kontextu mezi jádry přepne na výkon tohoto konkrétního vlákna.|

## <a name="see-also"></a>Viz také
- [Zobrazení jader](../profiling/cores-view.md)