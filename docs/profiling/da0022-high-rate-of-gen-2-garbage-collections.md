---
title: 'DA0022: Vysoká míra gen 2 sběru odpadků | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4e1fa46162f2aea74c5b3cb8396ad5e8d4c9a4cf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779373"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Vysoká míra 2. generace uvolňování pamětí

|||
|-|-|
|Id pravidla|DA0022 řekl:|
|Kategorie|Použití rozhraní .NET Framework|
|Metoda profilování|Všechny|
|Zpráva|Tam je poměrně vysoká míra Gen 2 uvolňování paměti dochází. Pokud podle návrhu většina datových struktur programu jsou přiděleny a trvalé po dlouhou dobu, to není obvykle problém. Pokud je však toto chování neúmyslné, aplikace může být připnutí objektů. Pokud si nejste jisti, můžete shromažďovat data přidělení paměti .NET a informace o životnosti objektu, abyste pochopili vzor přidělení paměti, který aplikace používá.|
|Typ pravidla|Upozornění|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="cause"></a>Příčina
 Data o výkonu systému, která byla shromážděna během profilování, naznačují, že významná část paměti for.NET framework objekty byla uvolněna v generaci 2 uvolňování paměti ve srovnání s generování 0 a generace 1 uvolňování paměti.

## <a name="rule-description"></a>Popis pravidla
 Microsoft .NET společný jazyk run-time (CLR) poskytuje mechanismus automatické správy paměti, který používá systém uvolňování paměti k uvolnění paměti z objektů, které aplikace již nepoužívá. Systém uvolňování paměti je orientován na generování na základě předpokladu, že mnoho přidělení jsou krátkodobé. Místní proměnné, například, by měl být krátkodobý. Nově vytvořené objekty spustit v generaci 0 (gen 0), a pak jejich průběh generace 1 při jejich přežití spuštění uvolňování paměti a nakonec přechod na generaci 2, pokud aplikace stále používá.

 Objekty v generaci 0 jsou shromažďovány často a obvykle velmi efektivně. Objekty v generaci 1 jsou shromažďovány méně často a méně efektivně. Nakonec by měly být objekty s dlouhou životností v generaci 2 shromažďovány ještě méně často. Generace 2 kolekce, která je úplné uvolnění paměti spustit, je také nejdražší operace.

 Toto pravidlo je aktivována, když proporcionálně dochází k příliš mnoho uvolnění paměti generace 2. Dobře vychované aplikace rozhraní .NET Framework budou mít více než 5krát více než mnoho uvolnění paměti generace 1 jako kolekce generace 2. (10x faktor je pravděpodobně ideální.)

## <a name="how-to-investigate-a-warning"></a>Jak prošetřit varování
 Poklepáním na zprávu v okně Seznam chyb přejděte do [zobrazení značek](../profiling/marks-view.md) dat profilování. Vyhledejte paměť **.NET\\CLR # kolekcí Gen 0** a **.NET CLR Memory\\# sloupců Gen 1 Collections.** Zjistěte, zda existují určité fáze provádění programu, kde dochází častěji. Porovnejte tyto hodnoty **s % čas ve sloupci GC** a zjistěte, zda vzor přidělení spravované paměti způsobuje nadměrnou režii správy paměti.

 Vysoký podíl uvolnění paměti generace 2 není vždy problém. Mohlo by to být záměrné. Aplikace, která přiděluje velké datové struktury, které musí zůstat aktivní po dlouhou dobu během provádění může aktivovat toto pravidlo. Pokud je taková aplikace pod tlakem paměti, může být vynuceno provádět časté uvolňování paměti. Pokud levnější generace 0 a generace 1 uvolnění paměti můžete kultivovat pouze malé množství spravované paměti, častější generace 2 uvolnění paměti bude naplánováno.

 Existují další sloupce paměti .NET CLR v zobrazení marks, které vám mohou pomoci identifikovat problémy s uvolňováním paměti. % **času ve** sloupci GC vám pomůže pochopit, kolik režie správy paměti dochází. Pokud vaše aplikace obvykle používá poměrně malý počet velkých, ale trvalých objektů, pak časté generace 2 kolekce by neměla spotřebovávat nadměrné množství času procesoru. Pokud je aplikace pod tlakem paměti, protože je vyžadováno více fyzické paměti (RAM), mohou se také spustit související pravidla, která vyhodnocují hodnoty **sloupců Memory\Pages/sec.**

 Chcete-li porozumět vzoru spravované paměti aplikace, profilovat jej znovu spuštěna.NET profilu přidělení paměti a vyberte možnost profilování Životnost objektu.

 Informace o tom, jak zlepšit výkon uvolňování paměti, naleznete v [tématu Základy uvolňování paměti a rady při výkonu](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) na webu společnosti Microsoft. Informace o režii automatického uvolňování paměti naleznete v [tématu Halda velkého objektu uncovered](https://msdn.microsoft.com/magazine/cc534993.aspx).
