---
title: DA0018-32-bitová aplikace spuštěná v limitech paměti spravovaného procesu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 74fed5f0dcbac45f603f16743eb2635fcf35292a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548145"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018:32-bitová aplikace spuštěná v limitech paměti spravovaného procesu

|Položka|Hodnota|
|-|-|
|ID pravidla|DA0018|
|Kategorie|Využití Nástroje pro profilaci|
|Metoda profilace|Vzorkování|
|Zpráva|Přidělení spravované paměti se blíží výchozímu limitu pro 32 proces. Vaše aplikace může být vázaná na paměť.|
|Typ pravidla|Upozornění|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.

## <a name="cause"></a>Příčina
 Systémová data shromážděná během procesu profilace označují, že haldy .NET Framework paměti dosáhly maximální velikosti, ke které mají spravované haldy přístup v 32m procesu. Tato maximální velikost je výchozí hodnota. Vychází z celkového množství adresního prostoru procesu, který se dá přidělit pro soukromé bajty. Hlášená hodnota je maximální zjištěná hodnota haldy během aktivního procesu profilace. Zvažte opětovné vytvoření profilace pomocí metody profilace paměti .NET a optimalizace použití spravovaných prostředků aplikací.

 Pokud velikost spravovaných hald přiblíží výchozímu limitu, může být potřeba vyvolat častěji proces automatického uvolňování paměti. Tím se zvyšuje režie správy paměti.

 Pravidlo se aktivuje jenom pro 32 aplikace běžící na 32 počítačích.

## <a name="rule-description"></a>Popis pravidla
 Modul CLR (Common Language Runtime) platformy Microsoft .NET poskytuje automatický mechanismus správy paměti, který používá systém uvolňování paměti k uvolnění paměti z objektů, které aplikace již nepoužívá. Systém uvolňování paměti je zaměřený na generaci, a to na základě předpokladu, že mnoho přidělení je krátkodobé. Místní proměnné, například by měly být krátkodobé. Nově vytvořené objekty začínají v generaci 0 (gen 0) a poté budou dokončeny na generaci 1, když přestanou běžet v uvolňování paměti, a nakonec přechod na generaci 2, pokud je aplikace stále používá.

 Spravované objekty, které jsou větší než 85 KB, jsou přidělovány Large Object haldě, kde se vztahují k méně častým uvolňováním paměti a komprimaci než menší objekty. velké objekty jsou spravovány samostatně, protože se předpokládá, že jsou trvalé a protože kombinace trvalých a velkých objektů s často přidělenými menšími objekty může způsobit fragmentaci haldy v horším přetypování.

 Vzhledem k tomu, že celková velikost spravovaných hald se blíží k výchozímu limitu, režie správy paměti obvykle roste na místo, kde může začít ovlivňovat odezvu a škálovatelnost aplikace.

## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění
 Dvojitým kliknutím na zprávu v okně Seznam chyb přejdete do zobrazení [značky](../profiling/marks-view.md) . Vyhledá **paměť .NET CLR \\ počet bajtů ve všech haldách** a sloupcích **# celkem potvrzených bajtů** . Určete, zda existují konkrétní fáze provádění programu, kde je přidělení spravované paměti těžší než jiné fáze. Porovnejte hodnoty ve sloupci **počet bajtů ve všech haldách** s frekvencí uvolňování paměti nahlášené v **paměti .NET CLR pro \\ kolekce 1**. generace, v **paměti .NET CLR \\ # z kolekcí 1**. generace a v **paměti .NET CLR. \\ # 2** . generace mají vliv na rychlost uvolňování paměti.

 V aplikaci .NET Framework modul CLR (Common Language Runtime) omezuje celkovou velikost spravovaných hald na méně než jednu polovinu maximální velikosti privátní oblasti v adresním prostoru procesu. Pro 32 procesy běžící na 32 počítači představuje 2 GB horní limit soukromé části adresního prostoru procesu. Vzhledem k tomu, že celková velikost spravovaných hald začíná pro přístup k jejímu výchozímu limitu, může dojít ke zvýšení režie správy paměti a snížení výkonu aplikace.

 Pokud se jedná o problém nadměrné nároky na spravovanou paměť, vezměte v úvahu jednu z těchto možností:

- optimalizace využití spravovaných paměťových prostředků aplikací

   -nebo-

- Postup uvolnění omezení architektury pro maximální velikost virtuální paměti pro 32 proces

  Chcete-li optimalizovat využití spravovaných paměťových prostředků aplikací, Shromážděte data přidělení spravované paměti v běhu profilování přidělení paměti .NET. Projděte si sestavy [zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md) , abyste pochopili, jaký je model přidělení paměti aplikace.

  Pomocí [zobrazení životnosti objektů](../profiling/object-lifetime-view.md) určete, který z datových objektů programu je v generaci, a pak se z něj uvolní.

  Pomocí [zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md) Určete cestu spuštění, která je výsledkem těchto přidělení.

  Další informace o tom, jak zlepšit výkon uvolňování paměti, najdete v článku .NET Framework technické články, [základy systému uvolňování paměti a tipy k výkonu](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) na webu MSDN.

  Chcete-li získat strukturální úlevy z omezení virtuální paměti na velikost soukromé části adresního prostoru procesu, zkuste spustit tento 32 proces na 64 počítači.  32 proces na 64 počítači může získat až 4 GB privátní virtuální paměti.

  64 proces, který běží na 64 počítači, může získat až 8 TB virtuální paměti. Zvažte opětovné kompilování aplikace, aby byla spuštěna jako nativní 64 aplikace. Toto pravidlo je pouze pro informace a nemusí vyžadovat nápravné akce.
