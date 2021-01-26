---
title: Sestava profilu spuštění | Microsoft Docs
description: Přečtěte si o sestavě profilu spuštění, což je tradiční profil vzorkování v rozšíření Vizualizátor souběžnosti pro Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 98361f9abad40e447d7198265d21ef193bb9ddf5
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801385"
---
# <a name="execution-profile-report"></a>Sestava profilu spuštění
Sestava profilu spuštění je tradiční profil vzorkování. Během období, kdy je vlákno spuštěno v logickém jádru, jsou vzorky vytvářeny přibližně každých milisekund a Vizualizér souběžnosti sestaví typický strom volání pomocí kompletování nahromaděné sady vzorových zásobníků. Data v této tabulce mohou být ovlivněna aktuálním časovým rozsahem a skrytými vlákny a těmito filtry, které mohou být aplikovány:

- Pokud je vybrána možnost Pouze můj kód, jsou zobrazeny pouze rámce zásobníku, které mají kód uživatele a jednu úroveň pod uživatelským kódem.

- Pokud je nastavená hodnota snížení šumu, odfiltrují se zásobníky, které mají míň, než je zadaná frekvence, ze sestavy.

  V následující tabulce jsou uvedeny sloupce v sestavě.

|Sloupec|Popis|
|------------|-----------------|
|Název|Název funkce pro každou úroveň zásobníku volání.|
|Vzorky včetně|Celkový počet vzorků, které jsou shromažďovány pro všechny zásobníky, které jsou zahrnuty do této úrovně stromu zásobníku volání. Celkové číslo (včetně) je součet exkluzivních vzorků pro tuto funkci a všechny čítače pro všechny podřízené uzly.|
|Exkluzivní vzorky|Celkový počet shromážděných vzorků, pro které je tato funkce nejnižší úrovní zásobníku volání.|
|% Včetně|Procentuální podíl z celkového počtu vzorků, který je zobrazen ve sloupci celkových vzorků. Procenta jsou zaokrouhlena na dvě desetinná místa.|
|% Exkluzivní|Procentuální podíl z celkového počtu vzorků, který je zobrazen ve sloupci výhradní vzorky. Procenta jsou zaokrouhlena na dvě desetinná místa.|
|Podrobnosti|Plně kvalifikovaný název funkce. To zahrnuje počet řádků, je-li k dispozici.|

 Tato tabulka sestavy je zobrazená v zobrazení [čas spuštění (zobrazení vlákna)](../profiling/execution-time-threads-view.md) .

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)