---
title: Pravidla výkonu .NET Framework využití | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ac78ffb3455940cf2379af44ff5c2bc5870dc684
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531999"
---
# <a name="net-framework-usage-performance-rules"></a>Pravidla výkonu použití rozhraní .NET Framework
Pravidla výkonu v kategorii použití the.NET Framework identifikují konkrétní metody, které je možné optimalizovat, a také identifikují obecnější vzory použití, jako je uvolňování paměti a kolize, které je možné prozkoumat kvůli problémům s výkonem.

|Pravidlo|Popis|
|-|-|
|[DA0001: Použití třídy StringBuilder ke zřetězení](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Volání na <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> jsou významné poměry dat profilování. Zvažte použití <xref:System.Text.StringBuilder> třídy pro sestavování řetězců z více segmentů.|
|[DA0005: Časté shromažďování GC2](../profiling/da0005-frequent-gc2-collections.md)|V uvolňování paměti 2. generace se uvolňuje poměrně vysoký počet objektů paměti .NET. Je-li příliš mnoho krátkodobých objektů po generaci 1 kolekce, náklady na správu paměti mohou být snadno velké.|
|[DA0006: Přepis Equals() pro typy hodnot](../profiling/da0006-override-equals-parens-for-value-types.md)|Volání `Equals` metody nebo operátorů rovnosti typu veřejné hodnoty jsou významným podílem dat profilování. Zvažte implementaci efektivnější metody.|
|[DA0007: Vyhnutí se použití výjimek pro tok řízení](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|V datech profilování byla volána vysoká míra .NET Framework obslužných rutin výjimek. Zvažte použití jiné logiky toku řízení k omezení počtu výjimek, které jsou vyvolány.|
|[DA0010: Náročná funkce GetHashCode](../profiling/da0010-expensive-gethashcode.md)|Volání `GetHashCode` metody typu jsou významným podílem dat profilování nebo `GetHashCode` Metoda přiděluje paměť. Snižte složitost metody.|
|[DA0011: Náročná funkce CompareTo](../profiling/da0011-expensive-compareto.md)|`CompareTo`Metoda typu je náročná nebo metoda přiděluje paměť. Snižte složitost `CompareTo` metody.|
|[DA0012: Velký počet reflexí](../profiling/da0012-significant-amount-of-reflection.md)|Volání metod, jako <xref:System.Reflection?displayProperty=fullName> <xref:System.Reflection.IReflect.InvokeMember%2A> <xref:System.Reflection.IReflect.GetMember%2A> jsou a nebo do metod typu, jako <xref:System.Type.InvokeMember%2A> jsou významné poměry dat profilování. Pokud je to možné, zvažte nahrazení těchto metod pomocí počáteční vazby na metody závislých sestavení.|
|[DA0013: Vysoký výskyt použití String.Split nebo String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Volání <xref:System.String.Split%2A?displayProperty=fullName> <xref:System.String.Substring%2A> metod nebo jsou významnou částí dat profilování. Zvažte použití <xref:System.String.IndexOf%2A> nebo, <xref:System.String.IndexOfAny%2A> Pokud testujete existenci podřetězce v řetězci.|
|[DA0018: 32bitová aplikace spuštěná v limitech paměti spravovaného procesu](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Systémová data shromažďovaná během procesu profilace označují, .NET Framework haldy paměti, které se blíží maximální velikosti, ke kterým mohou spravované haldy přistupovat v 32m procesu. Zvažte opětovné vytvoření profilace pomocí metody profilace paměti .NET a optimalizace použití spravovaných prostředků aplikací.|
|[DA0021: Vysoká míra 1. generace uvolňování paměti](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|V uvolňování paměti 1. generace se uvolňuje poměrně velký počet objektů paměti .NET. Pokud příliš mnoho krátkodobých objektů předrželo kolekci 0 generace, náklady na správu paměti mohou být snadno velké.|
|[DA0022: Vysoká míra 2. generace uvolňování paměti](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|V uvolňování paměti 2. generace se uvolňuje velký počet paměťových objektů .NET. Je-li příliš mnoho krátkodobých objektů po generaci 1 kolekce, náklady na správu paměti mohou být snadno velké. Toto pravidlo je vyvoláno, když frekvence kolizí zámků překročí horní prahovou hodnotu pravidla DA0005.|
|[DA0023: Vysoký čas procesoru uvolňování paměti](../profiling/da0023-high-gc-cpu-time.md)|Data o výkonu systému shromažďovaná během profilace označují, že množství času stráveného uvolňováním paměti je v porovnání s celkovou dobou zpracování aplikace významné.|
|[DA0024: Nadměrný čas procesoru uvolňování paměti](../profiling/da0024-excessive-gc-cpu-time.md)|Data o výkonu systému shromažďovaná během profilace označují, že množství času stráveného uvolňováním paměti je příliš vysoké v porovnání s celkovou dobou zpracování aplikace. Toto pravidlo je vyvoláno, když doba strávená uvolňováním paměti překračuje horní prahovou hodnotu DA0023 pravidla.|
|[DA0038: vysoká míra kolizí zámků](../profiling/da0038-high-rate-of-lock-contentions.md)|Data o výkonu systému shromážděná s daty profilace znamenají, že během provádění aplikace došlo k výraznému vysokému podílu kolizí zámků. Zvažte znovu profilaci pomocí metody profilace souběžnosti, abyste zjistili příčinu sporů.|
|[DA0039: velmi vysoká míra kolizí zámků](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Data o výkonu systému shromážděná s daty profilace znamenají, že během provádění aplikace došlo k nadměrné vysoké míře kolizí zámků. Zvažte znovu profilaci pomocí metody profilace souběžnosti, abyste zjistili příčinu sporů. Toto pravidlo je vyvoláno, když frekvence kolizí zámků překročí horní prahovou hodnotu pravidla DA0038.|
