---
title: 'DA0024: Nadměrný čas procesoru GC | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b8352095bcf31c137d391c2ed2e832d34e0ec7b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779347"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: Nadměrný čas procesoru GC

|||
|-|-|
|Id pravidla|DA0024 řekl:|
|Kategorie|Použití rozhraní .NET Framework|
|Metoda profilování|Všechny|
|Zpráva|% Čas v GC je velmi vysoký. Existuje nadměrné množství režie uvolňování paměti.|
|Typ pravidla|Upozornění|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="cause"></a>Příčina
 Data o výkonu systému, která byla shromážděna během profilování, označují, že doba strávená v uvolňování paměti je příliš vysoká ve srovnání s celkovou dobou zpracování aplikace.

## <a name="rule-description"></a>Popis pravidla
 Microsoft .NET společný jazyk run-time (CLR) poskytuje mechanismus automatické správy paměti, který používá systém uvolňování paměti k uvolnění paměti z objektů, které aplikace již nepoužívá. Systém uvolňování paměti je orientován na generování na základě předpokladu, že mnoho přidělení jsou krátkodobé. Místní proměnné, například, by měl být krátkodobý. Nově vytvořené objekty spustit v generaci 0 (gen 0), a pak jejich průběh generace 1 při jejich přežití spuštění uvolňování paměti a nakonec přechod na generaci 2, pokud aplikace stále používá.

 Objekty v generaci 0 jsou shromažďovány často a obvykle velmi efektivně. Objekty v generaci 1 jsou shromažďovány méně často a méně efektivně. Nakonec by měly být objekty s dlouhou životností v generaci 2 shromažďovány ještě méně často. Generace 2 kolekce, která je úplné uvolnění paměti spustit, je také nejdražší operace.

 Toto pravidlo je aktivována, když je příliš vysoká doba strávená v uvolňování paměti ve srovnání s celkovou dobou zpracování aplikace.

> [!NOTE]
> Pokud je podíl času stráveného v uvolňování paměti významný, ale není nadměrný ve srovnání s celkovou dobou zpracování aplikace, [da0023: Vysoká GC cpu čas](../profiling/da0023-high-gc-cpu-time.md) upozornění požáry namísto tohoto pravidla.

## <a name="how-to-investigate-a-warning"></a>Jak prošetřit varování
 Poklepáním na zprávu v okně Seznam chyb přejděte do [zobrazení značek](../profiling/marks-view.md) dat profilování. Vyhledejte ve sloupci **GC %čas paměti\\.NET CLR.** Zjistěte, zda existují určité fáze provádění programu, kde je režie uvolňování paměti spravované paměti těžší než jiné fáze. Porovnejte hodnoty % času v gc hodnotě s rychlostí uvolňování paměti **vykázanou**v # gen 0 Kolekce , **# gen 1 kolekce**hodnoty. **# of Gen 2 Collections**

 Hodnota % času v gc se pokusí ohlásit množství času, který aplikace stráví prováděním uvolňování paměti úměrně k celkovému množství zpracování. Uvědomte si, že existují okolnosti, kdy % čas v GC hodnota může vykazovat vysokou hodnotu, ale není z důvodu nadměrné uvolňování paměti. Další informace o způsobu výpočtu hodnoty % času v gc naleznete v [tématu Rozdíl mezi daty Perf hlášenými různými nástroji - 4](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) položka blogu **Maoni's Weblog** na MSDN. Pokud dochází k chybám stránky nebo je aplikace předem vypozdřena jinou vyšší prioritou práce na počítači během uvolňování paměti, % čas v GC čítač bude odrážet tyto další zpoždění.
