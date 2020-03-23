---
title: 'DA0005: Časté kolekce GC2 | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a50567a101d77ed6498aaae13a5fe5556d9c1056
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777709"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Časté shromažďování GC2

|||
|-|-|
|RuleId|DA0005 řekl:|
|Kategorie|Použití rozhraní .NET Framework|
|Metoda profilování|Paměť .NET|
|Zpráva|Mnoho objektů jsou shromažďovány v uvolnění paměti generace 2.|
|Typ zprávy|Upozornění|

## <a name="cause"></a>Příčina
 Vysoký počet objektů paměti .NET jsou uvolněny v uvolnění paměti generace 2.

## <a name="rule-description"></a>Popis pravidla
 Microsoft .NET společný jazyk runtime (CLR) poskytuje mechanismus automatické správy paměti, který používá systém uvolňování paměti k uvolnění paměti z objektů, které aplikace již nepoužívá. Systém uvolňování paměti je orientován na generování na základě předpokladu, že mnoho přidělení jsou krátkodobé. Místní proměnné, například, by měl být krátkodobý. Nově vytvořené objekty spustit v generaci 0 (gen 0), a pak jejich průběh generace 1 při jejich přežití spuštění uvolňování paměti a nakonec přechod na generaci 2, pokud aplikace stále používá.

 Objekty v generaci 0 jsou shromažďovány často a obvykle velmi efektivně. Objekty v generaci 1 jsou shromažďovány méně často a méně efektivně. Nakonec by měly být objekty s dlouhou životností v generaci 2 shromažďovány ještě méně často. Generace 2 kolekce, která je úplné uvolnění paměti spustit, je také nejdražší operace.

 Toto pravidlo je aktivováno, pokud došlo k proporcionálně příliš mnoho uvolnění paměti generace 2. Pokud příliš mnoho relativně krátkodobé objekty přežít generace 1 kolekce, ale pak mohou být shromažďovány v generaci 2 úplné kolekce, náklady na správu paměti může snadno stát nadměrné. Další informace naleznete v krizovém příspěvku [v polovině života](https://blogs.msdn.microsoft.com/ricom/2003/12/04/mid-life-crisis/) na webu MSDN společnosti Rico Mariani's Performance Tidbits.

## <a name="how-to-investigate-a-warning"></a>Jak prošetřit varování
 Zkontrolujte sestavy [zobrazení paměti .NET,](../profiling/dotnet-memory-data-views.md) abyste pochopili vzor přidělení paměti aplikace. Pomocí [zobrazení životnosti objektu](../profiling/object-lifetime-view.md) určete, které datové objekty programu přežívají do generace 2 a odtud jsou znovu vyzvednuty. Pomocí [zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md) určete cestu spuštění, která vedla k těmto přidělením.

 Informace o tom, jak zlepšit výkon uvolňování paměti, naleznete v [tématu Základy uvolňování paměti a rady při výkonu](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) na webu společnosti Microsoft. Informace o režii automatického uvolňování paměti naleznete v [tématu Halda velkého objektu uncovered](https://msdn.microsoft.com/magazine/cc534993.aspx).
