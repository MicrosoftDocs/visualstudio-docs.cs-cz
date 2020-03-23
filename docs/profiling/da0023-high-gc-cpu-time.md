---
title: 'DA0023: Vysoká GC CPU čas | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f0dd45486f526954d7dfce45cd607ff6196eae00
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777644"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Vysoký čas procesoru uvolňování paměti

|||
|-|-|
|Id pravidla|DA0023 řekl:|
|Kategorie|Použití rozhraní .NET Framework|
|Metoda profilování|Všechny|
|Zpráva|% Čas v GC je poměrně vysoký. Tato indikace nadměrné množství režie uvolňování paměti může mít vliv na odezvu aplikace. Můžete shromažďovat data přidělení paměti .NET a informace o životnosti objektu, abyste pochopili vzor přidělení paměti, který aplikace lépe používá.|
|Typ pravidla|Informační|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="cause"></a>Příčina
 Data o výkonu systému, která jsou shromažďována během profilování označuje, že množství času stráveného v uvolňování paměti je významné ve srovnání s celkovou dobu zpracování aplikace.

## <a name="rule-description"></a>Popis pravidla
 Microsoft .NET společný jazyk run-time (CLR) poskytuje mechanismus automatické správy paměti, který používá systém uvolňování paměti k uvolnění paměti z objektů, které aplikace již nepoužívá. Systém uvolňování paměti je orientován na generování na základě předpokladu, že mnoho přidělení jsou krátkodobé. Místní proměnné, například, by měl být krátkodobý. Nově vytvořené objekty spustit v generaci 0 (gen 0), a pak jejich průběh generace 1 při jejich přežití spuštění uvolňování paměti a nakonec přechod na generaci 2, pokud aplikace stále používá.

 Objekty v generaci 0 jsou shromažďovány často a efektivně. Objekty v generaci 1 jsou shromažďovány méně často a méně efektivně. Nakonec by měly být objekty s dlouhou životností v generaci 2 shromažďovány ještě méně často. Generace 2 kolekce, která je úplné uvolnění paměti spustit, je také nejdražší operace.

 Toto pravidlo je aktivována, když množství času stráveného v uvolňování paměti je významné ve srovnání s celkovou dobu zpracování aplikace.

> [!NOTE]
> Pokud je podíl času stráveného v uvolňování paměti nadměrný ve srovnání s celkovou dobou zpracování aplikace, [da0024: Nadměrné GC čas procesoru](../profiling/da0024-excessive-gc-cpu-time.md) upozornění požáry namísto tohoto pravidla.

## <a name="how-to-investigate-a-warning"></a>Jak prošetřit varování
 Poklepáním na zprávu v okně Seznam chyb přejděte do [zobrazení značek](../profiling/marks-view.md) dat profilování. Vyhledejte ve sloupci **GC %čas paměti\\.NET CLR.** Zjistěte, zda existují určité fáze provádění programu, kde je režie uvolňování paměti spravované paměti těžší než jiné fáze. Porovnejte hodnoty % času v gc hodnotě s rychlostí uvolňování paměti **vykázanou**v # gen 0 Kolekce , **# gen 1 kolekce**hodnoty. **# of Gen 2 Collections**

 Hodnota % času v gc se pokusí ohlásit množství času, který aplikace stráví prováděním uvolňování paměti úměrně k celkovému množství zpracování. Uvědomte si, že existují okolnosti, kdy % čas v GC hodnota může vykazovat vysokou hodnotu, ale není z důvodu nadměrné uvolňování paměti. Další informace o způsobu výpočtu hodnoty % času v gc naleznete v [tématu Rozdíl mezi daty Perf hlášenými různými nástroji - 4](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) položka blogu **Maoni's Weblog** na MSDN. Pokud dochází k chybám stránky nebo je aplikace znehybněna jinou vyšší prioritou práce na počítači během uvolňování paměti, % čas v GC čítače bude odrážet tyto další zpoždění.
