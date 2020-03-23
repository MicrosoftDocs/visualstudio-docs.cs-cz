---
title: 'DA0021: Vysoká míra gen 1 sběru paměti | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 36350b59a3d70f8553fddc5f58bf5c79716fa3aa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777657"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Vysoká míra 1. generace uvolňování pamětí

|||
|-|-|
|Id pravidla|DA0021 řekl:|
|Kategorie|Použití rozhraní .NET Framework|
|Metody profilování|Všechny|
|Zpráva|Existuje poměrně vysoká míra Gen 1 uvolňování paměti dochází. Pokud podle návrhu většina datových struktur programu jsou přiděleny a trvalé po dlouhou dobu, to není obvykle problém. Pokud je však toto chování neúmyslné, aplikace může být připnutí objektů. Pokud si nejste jisti, můžete shromažďovat data přidělení paměti .NET a informace o životnosti objektu, abyste pochopili vzor přidělení paměti, který aplikace používá.|
|Typ pravidla|Informace|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="cause"></a>Příčina
 Data o výkonu systému, která byla shromážděna během profilování, naznačují, že významná část paměťových objektů for.NET Framework byla uvolněna v generaci 1 uvolňování paměti ve srovnání se shromažďováním dat generace 0.

## <a name="rule-description"></a>Popis pravidla
 Microsoft .NET společný jazyk run-time (CLR) poskytuje mechanismus automatické správy paměti, který používá systém uvolňování paměti k uvolnění paměti z objektů, které aplikace již nepoužívá. Systém uvolňování paměti je orientován na generování na základě předpokladu, že mnoho přidělení jsou krátkodobé. Místní proměnné, například, by měl být krátkodobý. Nově vytvořené objekty spustit v generaci 0 (gen 0), a pak jejich průběh generace 1 při jejich přežití spuštění uvolňování paměti a nakonec přechod na generaci 2, pokud aplikace stále používá.

 Objekty v generaci 0 jsou shromažďovány často a obvykle velmi efektivně. Objekty v generaci 1 jsou shromažďovány méně často a méně efektivně. Nakonec by měly být objekty s dlouhou životností v generaci 2 shromažďovány ještě méně často. Generace 2 kolekce, která je úplné uvolnění paměti spustit, je také nejdražší operace.

 Toto pravidlo je aktivováno, pokud došlo k proporcionálně příliš mnoho uvolnění paměti generace 1. Pokud příliš mnoho poměrně krátkodobé objekty přežít generace 0 kolekce, ale pak mohou být shromažďovány v generaci 1 kolekce, náklady na správu paměti může být nadměrné. Další informace naleznete v krizovém příspěvku [v polovině života](https://blogs.msdn.microsoft.com/ricom/2003/12/04/mid-life-crisis/) na webu MSDN společnosti Rico Mariani's Performance Tidbits.

## <a name="how-to-investigate-a-warning"></a>Jak prošetřit varování
 Poklepáním na zprávu v okně Seznam chyb přejděte do [zobrazení značek](../profiling/marks-view.md) dat profilování. Vyhledejte paměť **.NET\\CLR # kolekcí Gen 0** a **.NET CLR Memory\\# sloupců Gen 1 Collections.** Zjistěte, zda existují určité fáze provádění programu, kde dochází častěji. Porovnejte tyto hodnoty **s % čas ve sloupci GC** a zjistěte, zda vzor přidělení spravované paměti způsobuje nadměrnou režii správy paměti.

 Chcete-li porozumět vzoru aplikace využití spravované paměti, profil ovat jej znovu spuštěn a.NET paměť ový profil a požádat o měření životnosti objektu.

 Informace o tom, jak zlepšit výkon uvolňování paměti, naleznete v [tématu Základy uvolňování paměti a rady při výkonu](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) na webu společnosti Microsoft. Informace o režii automatického uvolňování paměti naleznete v [tématu Halda velkého objektu uncovered](https://msdn.microsoft.com/magazine/cc534993.aspx).
