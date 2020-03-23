---
title: Sestava profilu provádění | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25886ad4f7c31ea02c8dab2d45d8709a362a5a69
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969989"
---
# <a name="execution-profile-report"></a>Sestava profilu spuštění
Sestava profilu spuštění je tradiční profil vzorkování. Vzorky jsou odebrány přibližně každou milisekundu během období, kdy je vlákno spuštěno na logickém jádru a vizualizér souběžnosti vytvoří typický strom volání tím, že sestavuje nahromaděnou sadu zásobníků vzorků. Data v této tabulce mohou být ovlivněna aktuálním časovým rozsahem a skrytými vlákny a těmito filtry, které mohou být použity:

- Pokud je vybrána možnost Jen můj kód, zobrazí se pouze rámce zásobníku, které mají uživatelský kód a o jednu úroveň pod uživatelským kódem.

- Pokud je nastavena hodnota snížení šumu, jsou z sestavy odfiltrovány kompletované zásobníky, které mají menší než zadaná frekvence.

  V následující tabulce jsou uvedeny sloupce v sestavě.

|Sloupec|Popis|
|------------|-----------------|
|Name (Název)|Název funkce pro každou úroveň zásobníku volání.|
|Včetně vzorků|Celkový počet vzorků, které jsou shromažďovány pro všechny zásobníky, které se shrnou do této úrovně stromu zásobníku volání. Včetně číslo je součet výhradní vzorky pro tuto funkci a včetně čítače pro všechny jeho podřízené uzly.|
|Exkluzivní ukázky|Celkový počet odebraných vzorků, pro které je tato funkce nejnižší úrovní zásobníku volání.|
|% včetně|Procento celkových vzorků, které je zobrazeno ve sloupci včetně vzorků. Procenta se zaokrouhlí na dvě desetinná místa.|
|% Exkluzivní|Procento celkových vzorků, které je zobrazeno ve sloupci výhradní vzorky. Procenta se zaokrouhlí na dvě desetinná místa.|
|Podrobnosti|Plně kvalifikovaný název funkce. To zahrnuje počet řádků, pokud je k dispozici.|

 Tuto tabulku sestavy lze zobrazit v zobrazení [Doba spuštění (zobrazení vláken).](../profiling/execution-time-threads-view.md)

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)