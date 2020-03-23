---
title: 'DA0018: 32bitová aplikace spuštěná při omezení chované paměti procesu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: d7bebd25f499131b4beda109ebb9ac468c2435b1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780062"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018: 32bitová aplikace spuštěná s omezením paměti spravované procesem

|||
|-|-|
|Id pravidla|DA0018|
|Kategorie|Využití nástrojů profilování|
|Metoda profilování|Vzorkování|
|Zpráva|Přidělení spravované paměti blížící se výchozímu limitu pro 32bitový proces. Aplikace může být vázána na paměť.|
|Typ pravidla|Upozornění|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="cause"></a>Příčina
 Systémová data shromážděná během profilování znamená, že hromady paměti rozhraní .NET Framework se přiblížily maximální velikosti, které mohou spravované hromady dosáhnout v 32bitovém procesu. Tato maximální velikost je výchozí hodnota. Je založen na celkové mno ství adresního prostoru procesu, který lze přidělit soukromým bajtům. Vykázaná hodnota je maximální pozorovaná hodnota hromad, zatímco profilovaný proces byl aktivní. Zvažte profilování znovu pomocí metody profilování paměti .NET a optimalizaci použití spravovaných prostředků aplikací.

 Při velikosti spravované hromady přístup výchozí limit, proces automatické uvolňování paměti může být vyvolána častěji. To zvyšuje režii správy paměti.

 Pravidlo pouze pro 32bitové aplikace spuštěné na 32bitových počítačích.

## <a name="rule-description"></a>Popis pravidla
 Microsoft .NET společný jazyk run-time (CLR) poskytuje mechanismus automatické správy paměti, který používá systém uvolňování paměti k uvolnění paměti z objektů, které aplikace již nepoužívá. Systém uvolňování paměti je orientován na generování na základě předpokladu, že mnoho přidělení jsou krátkodobé. Místní proměnné, například, by měl být krátkodobý. Nově vytvořené objekty spustit v generaci 0 (gen 0), a pak jejich průběh generace 1 při jejich přežití spuštění uvolňování paměti a nakonec přechod na generaci 2, pokud aplikace stále používá.

 Spravované objekty, které jsou větší než 85 kB jsou přiděleny na haldy velkého objektu, kde jsou předmětem méně časté uvolňování paměti a zhutnění než menší objekty. velké objekty jsou spravovány samostatně, protože se předpokládá, že jsou trvalejší a protože míchání trvalé a velké objekty s často přidělené menší objekty může způsobit nejhorší přetypování fragmentace haldy.

 Jako celková velikost spravované hromady přístup výchozí limit, režie správy paměti obvykle zvyšuje do bodu, kde může začít mít vliv na odezvu a škálovatelnost aplikace.

## <a name="how-to-investigate-a-warning"></a>Jak prošetřit varování
 Poklepáním na zprávu v okně Seznam chyb přejděte do zobrazení [Značky.](../profiling/marks-view.md) Najít **.NET CLR\\paměti # bajty ve všech hromady** a **# Celkem potvrzených bajtů** sloupce. Zjistěte, zda existují určité fáze provádění programu, kde je přidělení spravované paměti těžší než jiné fáze. Porovnejte hodnoty **# Bajty ve všech hedžových** sloupcích s rychlostí uvolňování paměti vykázané v **paměti\\.NET CLR # kolekcí Gen 0**, paměti **.NET CLR\\# kolekcí Gen 1**a **.NET CLR Memory\\# sloupců Gen 2 Collections,** abyste zjistili, zda vzorek přidělení spravované paměti ovlivňuje rychlost uvolňování paměti.

 V aplikaci rozhraní .NET Framework čas common language runtime omezuje celkovou velikost spravovaných hromad na o něco menší než polovinu maximální velikosti soukromé části prostoru adresního prostoru procesu. Pro 32bitové procesy spuštěné na 32bitovém počítači představuje 2 GB horní limit soukromé části adresního prostoru procesu. Jako celková velikost spravované hromady začne blížit jeho výchozí limit, režie správy paměti může zvýšit a výkon aplikace může snížit.

 Pokud je problém s nadměrnou režií spravované paměti, zvažte některou z těchto možností:

- optimalizace využití prostředků spravované paměti aplikací

   -nebo-

- podniknutí kroků ke zmírnění architektonických omezení maximální velikosti virtuální paměti pro 32bitový proces

  Chcete-li optimalizovat využití prostředků spravované paměti aplikací, shromážděte data přidělení spravované paměti v systému profilování přidělení paměti .NET. Zkontrolujte sestavy [zobrazení paměti .NET,](../profiling/dotnet-memory-data-views.md) abyste pochopili vzor přidělení paměti aplikace.

  Pomocí [zobrazení životnosti objektu](../profiling/object-lifetime-view.md) určete, které datové objekty programu přežívají do generování a pak jsou odtud rekultivovány.

  Pomocí [zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md) určete cestu spuštění, která vedla k těmto přidělením.

  Další informace o tom, jak zlepšit výkon uvolňování paměti, naleznete v technickém článku rozhraní .NET [Framework, Garbage Collector Basics a Performance Hints](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) na webu MSDN.

  Chcete-li získat odlehčení architektury od omezení virtuální paměti na velikost soukromé části adresního prostoru procesu, zkuste spustit tento 32bitový proces v 64bitovém počítači.  32bitový proces v 64bitovém počítači může získat až 4 GB privátní virtuální paměti.

  64bitový proces spuštěný na 64bitovém počítači může získat až 8 TB virtuální paměti. Zvažte rekompilaci aplikace ke spuštění jako nativní 64bitová aplikace. Toto pravidlo je pouze pro informaci a nemusí vyžadovat nápravná opatření.
