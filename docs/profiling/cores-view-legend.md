---
title: Legenda zobrazení jader | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62553160"
---
# <a name="cores-view-legend"></a>Legenda zobrazení jader
Legenda zobrazení jádra identifikuje jednotlivá vlákna podle barvy a názvu. Obsahuje sloupce, které zobrazují počty pro přepnutí kontextu mezi jádry, celkový počet přepínačů kontextu a procento přepínačů kontextu, které kříží jádro. Řádky v legendě jsou seřazené podle počtu přepínačů kontextu křížového jádra v klesajícím pořadí.

 Můžete vybrat řádky v legendě a filtrovat tak vlákna, která se zobrazují na časové ose. Na časové ose se zobrazí pouze vybraná vlákna. Pokud nevyberete žádné řádky, na časové ose se zobrazí všechny řádky.

 Kontext křížového jádra přepíná náklady větší v režii a výkonu než přepínače, které zůstávají ve stejném logickém jádru. Během přepínání kontextu se Registry procesoru ukládají a obnovují, kód jádra operačního systému se spustí, položky vyrovnávací paměti TLB překladu se znovu načítají a kanál procesoru se vyprázdní. Přepnutí kontextu mezi jádry můžou být ještě dražší než ostatní přepínače kontextu, protože data mezipaměti nejsou platná pro toto vlákno v jiném jádru. Na rozdíl od toho, pokud je vlákno kontextově přepnuto na jádro, na kterém dříve běželo, je pravděpodobnější, že jsou užitečná data stále v mezipaměti. Pokud se přepnutí kontextu mezi jádry zvýšily o pokusům o správu spřažení vlákna a výkonu, zvažte, jestli se má tento problém vyřešit. Začněte tím, že Eliminujte spřažení vlákna, a pak Sledujte výsledné chování křížového jádra.

 Následující tabulka popisuje prvky legendy.

|Prvek|Definice|
|-------------|----------------|
|Název vlákna|Zobrazuje barvu vlákna v předchozí časové ose jader a název tohoto vlákna.|
|Přepnutí kontextu mezi jádry|Počet přepínačů kontextu pro vlákno, které je také přepnuto z jednoho logického jádra do jiného. Nerozlišuje mezi přepínači v kontextu mezi jádry, které jsou mezi jednotlivými procesory, a dalšími uživateli, které zůstávají na stejné kostce.|
|Celkový počet přepínačů kontextu|Celkový počet přepínačů kontextu pro dané vlákno během období vzorkování. Pokaždé, když dojde ke změně kontextu vlákna (například z spuštění na synchronizaci) se počítá jeden kontextový přepínač.|
|Procento přepínačů kontextu mezi jádry|Vypočítáno jako procento vydělením počtu přepínačů kontextu křížového jádra o počet přepínačů celkového kontextu. Čím vyšší je toto procento, tím větší je celkový účinek režie mezi přepínači kontextu mezi jádry a výkonem tohoto konkrétního vlákna.|

## <a name="see-also"></a>Viz také
- [Zobrazení jader](../profiling/cores-view.md)