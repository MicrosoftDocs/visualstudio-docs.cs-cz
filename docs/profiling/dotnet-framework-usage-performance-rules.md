---
title: Pravidla výkonu využití rozhraní .NET Framework | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5a740885d8876398bf86e279aa259e9169fcf7c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779284"
---
# <a name="net-framework-usage-performance-rules"></a>Pravidla výkonu použití rozhraní .NET Framework
Pravidla výkonu v kategorii the.NET použití rozhraní identifikují konkrétní metody, které lze optimalizovat, a také identifikují obecnější vzorce použití, jako je například uvolňování paměti a konflikty zámků, které lze prozkoumat problémy s výkonem.

|||
|-|-|
|[DA0001: Pro řetězení používejte StringBuilder](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Volání <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> jsou významnou částí dat profilování. Zvažte <xref:System.Text.StringBuilder> použití třídy k vytvoření řetězců z více segmentů.|
|[DA0005: Časté shromažďování GC2](../profiling/da0005-frequent-gc2-collections.md)|Relativně vysoký počet objektů paměti .NET jsou uvolněny v uvolnění paměti generace 2. Pokud příliš mnoho objektů s krátkou životností přežít generace 1 kolekce, náklady na správu paměti může snadno stát nadměrné.|
|[DA0006: Přepište Equals() pro hodnoty](../profiling/da0006-override-equals-parens-for-value-types.md)|Volání `Equals` metody nebo operátory rovnosti veřejného typu hodnoty jsou významnou částí dat profilování. Zvažte implementaci efektivnější metody.|
|[DA0007: Vyhněte se použití výjimek pro tok řízení](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|V datech profilování byla volána vysoká míra obslužných rutin výjimek rozhraní .NET Framework. Zvažte použití jiné logiky toku ovládacího prvku ke snížení počtu výjimek, které jsou vyvolány.|
|[DA0010: Náročná metoda GetHashCode](../profiling/da0010-expensive-gethashcode.md)|Volání `GetHashCode` metody typu jsou významnou část profilování dat `GetHashCode` nebo metoda přiděluje paměť. Snižte složitost metody.|
|[DA0011: Náročná metoda CompareTo](../profiling/da0011-expensive-compareto.md)|Metoda `CompareTo` typu je nákladné nebo metoda přiděluje paměť. Snižte složitost `CompareTo` metody.|
|[DA0012: Vysoký objem odrazů](../profiling/da0012-significant-amount-of-reflection.md)|Volání <xref:System.Reflection?displayProperty=fullName> metody jako <xref:System.Reflection.IReflect.InvokeMember%2A> a <xref:System.Reflection.IReflect.GetMember%2A> nebo Type metody, jako <xref:System.Type.InvokeMember%2A> jsou významné části profilování dat. Pokud je to možné, zvažte nahrazení těchto metod časnou vazbou na metody závislých sestavení.|
|[DA0013: Vysoké použití String.Split nebo String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Volání <xref:System.String.Split%2A?displayProperty=fullName> metody <xref:System.String.Substring%2A> or jsou významnou částí dat profilování. Zvažte <xref:System.String.IndexOf%2A> <xref:System.String.IndexOfAny%2A> použití nebo pokud testujete existenci podřetězce v řetězci.|
|[DA0018: 32bitová aplikace spuštěná v limitech paměti spravovaného procesu](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Systémová data shromážděná během profilování označují, že hromady paměti rozhraní .NET Framework se přiblížily maximální velikosti, které mohou spravované hromady dosáhnout v 32bitovém procesu. Zvažte profilování znovu pomocí metody profilování paměti .NET a optimalizaci použití spravovaných prostředků aplikací.|
|[DA0021: Vysoká míra 1. generace kolekce pamětí](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Relativně vysoký počet objektů paměti .NET jsou uvolněny v uvolnění paměti generace 1. Pokud příliš mnoho objektů s krátkou životností přežít generace 0 kolekce, náklady na správu paměti může snadno stát nadměrné.|
|[DA0022: Vysoká míra 2. generace uvolňování pamětí](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Vysoký počet objektů paměti .NET jsou uvolněny v uvolnění paměti generace 2. Pokud příliš mnoho objektů s krátkou životností přežít generace 1 kolekce, náklady na správu paměti může snadno stát nadměrné. Toto pravidlo je aktivováno, když rychlost kolizí zámku překročí horní prahovou hodnotu pravidla DA0005.|
|[DA0023: Vysoký čas procesoru uvolňování paměti](../profiling/da0023-high-gc-cpu-time.md)|Data o výkonu systému, která jsou shromažďována během profilování označuje, že množství času stráveného v uvolňování paměti je významné ve srovnání s celkovou dobu zpracování aplikace.|
|[DA0024: Nadměrný čas procesoru GC](../profiling/da0024-excessive-gc-cpu-time.md)|Data o výkonu systému, která jsou shromažďována během profilování označuje, že množství času stráveného v uvolňování paměti je příliš vysoká ve srovnání s celkovou dobu zpracování aplikace. Toto pravidlo je aktivováno, když množství času stráveného v uvolňování paměti překročí horní prahovou hodnotu pravidla DA0023.|
|[DA0038: Vysoká míra tvrzení o zámku](../profiling/da0038-high-rate-of-lock-contentions.md)|Data o výkonu systému, která jsou shromažďována s daty profilování označuje, že výrazně vysoká míra uzamčení konflikty došlo během provádění aplikace. Zvažte profilování znovu pomocí metody profilování souběžnosti k nalezení příčiny tvrzení.|
|[DA0039: Velmi vysoká míra tvrzení o zámku](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Data o výkonu systému, která jsou shromažďována s daty profilování označuje, že během provádění aplikace došlo k příliš vysoké míře konfliktů zámků. Zvažte profilování znovu pomocí metody profilování souběžnosti k nalezení příčiny tvrzení. Toto pravidlo je aktivováno, když rychlost kolizí zámku překročí horní prahovou hodnotu pravidla DA0038.|
