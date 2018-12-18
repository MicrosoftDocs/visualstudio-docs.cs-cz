---
title: Pravidla výkonu použití rozhraní .NET framework | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1903b61fce39bdd68b471472530857d720bac906
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766019"
---
# <a name="net-framework-usage-performance-rules"></a>Pravidla výkonu použití rozhraní .NET Framework
Pravidla výkonu v rozhraní.NET Framework využití kategorii identifikovat konkrétní metody, které lze optimalizovat a také určit další obecné vzorce použití, jako je například uvolňování paměti a spory uzamčení, který můžete prozkoumat pro problémy s výkonem.  
  
|||  
|-|-|  
|[DA0001: Pro řetězení používejte StringBuilder](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Volání <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> podstatnou část data profilování jsou. Zvažte použití <xref:System.Text.StringBuilder> třída k vytvoření řetězce z více segmentech.|  
|[DA0005: Časté kolekce GC2](../profiling/da0005-frequent-gc2-collections.md)|Relativně velké množství paměti objekty .NET jsou se uvolní v uvolňování paměti generace 2. Pokud příliš mnoho objektů krátkodobou zůstanou platné i po 1. generace kolekce, náklady na správu paměti můžete snadno stát nadměrné.|  
|[DA0006: Přepište Equals() pro hodnoty](../profiling/da0006-override-equals-parens-for-value-types.md)|Volání `Equals` podstatnou část data profilování jsou metoda nebo operátory rovnosti hodnota veřejného typu. Zvažte implementaci efektivnější metoda.|  
|[DA0007: Vyhněte se použití výjimek pro tok řízení](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|V profilaci data měla volat vysokou míru obslužné rutiny výjimek rozhraní .NET Framework. Zvažte použití jiných logiku toku řízení a snížit počet výjimky, které jsou vydány.|  
|[DA0010: Náročná metoda GetHashCode](../profiling/da0010-expensive-gethashcode.md)|Volání `GetHashCode` podstatnou část data profilování jsou metoda typu nebo `GetHashCode` metoda přidělí paměť. Snížit složitost metody.|  
|[DA0011: Náročná metoda CompareTo](../profiling/da0011-expensive-compareto.md)|`CompareTo` Metoda typu je nákladná, nebo metodu přidělí paměť. Snížení složitosti `CompareTo` metoda.|  
|[DA0012: Vysoký objem odrazů](../profiling/da0012-significant-amount-of-reflection.md)|Volání <xref:System.Reflection?displayProperty=fullName> metody, jako <xref:System.Reflection.IReflect.InvokeMember%2A> a <xref:System.Reflection.IReflect.GetMember%2A> nebo typ metody, jako <xref:System.Type.InvokeMember%2A> podstatnou část data profilování jsou. Pokud je to možné, zvažte nahrazení tyto metody časná vazba metody závislá sestavení.|  
|[DA0013: Vysoké použití String.Split nebo String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Volání <xref:System.String.Split%2A?displayProperty=fullName> nebo <xref:System.String.Substring%2A> podstatnou část data profilování jsou metody. Zvažte použití <xref:System.String.IndexOf%2A> nebo <xref:System.String.IndexOfAny%2A> Pokud testujete existenci substring v řetězci.|  
|[DA0018: 32bitová aplikace spuštěná v limitech paměti spravovaného procesu](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Data systému, která se shromažďují při spuštění profilování udává že paměti rozhraní .NET Framework haldách dosaženy maximální velikost, spravované haldách dosáhnout v 32bitový proces. Vezměte v úvahu profilace znovu pomocí metody profilace paměti .NET a optimalizace použití spravované prostředky v aplikaci.|  
|[DA0021: Vysoká míra 1. generace kolekce pamětí](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Relativně velké množství paměti objekty .NET jsou se uvolní v uvolňování paměti generace 1. Pokud příliš mnoho objektů krátkodobou zůstanou platné i po 0. generace kolekce, můžete snadno stanou se náklady na správu paměti nadměrné.|  
|[DA0022: Vysoká míra 2. generace kolekce pamětí](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Vysoký počet objekty paměti .NET jsou se uvolní v uvolňování paměti generace 2. Pokud příliš mnoho objektů krátkodobou zůstanou platné i po 1. generace kolekce, náklady na správu paměti můžete snadno stát nadměrné. Toto pravidlo aktivuje se v případě míra kolizí zámků překročí vyšší prahová hodnota pravidla DA0005.|  
|[DA0023: Vysoký čas procesoru uvolňování paměti](../profiling/da0023-high-gc-cpu-time.md)|Data výkonu systému, která se shromažďují při vytváření profilu označuje, že množství času stráveného v uvolňování paměti je důležité ve srovnání s časem zpracování celkový počet aplikací.|  
|[DA0024: Čas nadměrný procesoru uvolňování paměti](../profiling/da0024-excessive-gc-cpu-time.md)|Data výkonu systému, která se shromažďují při vytváření profilu označuje, že množství času stráveného v uvolňování paměti je příliš vysoké ve srovnání s časem zpracování celkový počet aplikací. Toto pravidlo aktivuje se v případě vyšší prahová hodnota pravidla DA0023 přesahuje množství času strávené v uvolňování paměti.|  
|[DA0038: Vysoká míra kolizí zámků](../profiling/da0038-high-rate-of-lock-contentions.md)|Systém data výkonu, která se shromažďují se data profilování označuje, že výrazně vysoká míra kolizí zámků došlo k chybě při spuštění aplikace. Vezměte v úvahu profilace znovu pomocí metoda profilování souběžného zpracování nalézt příčinu kolizí.|  
|[DA0039: Velmi vysoká míra kolizí zámků](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Systém data výkonu, která se shromažďují se data profilování označuje, že nadměrně vysoká míra kolizí zámků došlo k chybě při spuštění aplikace. Vezměte v úvahu profilace znovu pomocí metoda profilování souběžného zpracování nalézt příčinu kolizí. Toto pravidlo aktivuje se v případě míra kolizí zámků překročí vyšší prahová hodnota pravidla DA0038.|