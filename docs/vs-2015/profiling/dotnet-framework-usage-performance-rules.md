---
title: Pravidla výkonu použití rozhraní .NET framework | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0706a5279a2ab338cc6e50cce25051b4fba7b366
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756145"
---
# <a name="net-framework-usage-performance-rules"></a>Pravidla výkonu použití rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pravidla výkonu v rozhraní.NET Framework využití kategorii identifikovat konkrétní metody, které se dá optimalizovat a také identifikovat další obecné vzorce používání, jako je například uvolňování paměti a kolize zámků, které můžete prozkoumat pro problémy s výkonem.  
  
|||  
|-|-|  
|[DA0001: Pro řetězení používejte StringBuilder](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Volání <xref:System.String.Concat%28System.String%2CSystem.String%29?displayProperty=fullName> jsou podstatnou část dat profilování. Zvažte použití <xref:System.Text.StringBuilder> třídy k vytvoření řetězce z více segmentů.|  
|[DA0005: Časté kolekce GC2](../profiling/da0005-frequent-gc2-collections.md)|Relativně velké množství paměti objektů .NET jsou právě uvolněny v procesu uvolnění paměti generace 2. Pokud příliš mnoho krátkodobé objekty byly zachovány při 1. generace kolekce, náklady na správu paměti se snadno můžou stát nadměrné.|  
|[DA0006: Přepište Equals() pro hodnoty](../profiling/da0006-override-equals-parens-for-value-types.md)|Volání `Equals` metoda nebo operátory rovnosti veřejné hodnotového typu je podstatnou část dat profilování. Zvažte implementaci metodu efektivnější.|  
|[DA0007: Vyhněte se použití výjimek pro tok řízení](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Vysoký počet obslužných rutin výjimek rozhraní .NET Framework byly volány v dat profilování. Zvažte použití další logiku toku řízení k omezení počtu výjimek, které jsou vyvolány.|  
|[DA0010: Náročná metoda GetHashCode](../profiling/da0010-expensive-gethashcode.md)|Volání `GetHashCode` podstatnou část dat profilování jsou metody typu nebo `GetHashCode` metoda přidělí paměť. Zjednodušit metody.|  
|[DA0011: Náročná metoda CompareTo](../profiling/da0011-expensive-compareto.md)|`CompareTo` Metoda typu je nákladné nebo metodu přidělí paměť. Vám pomůže zjednodušit `CompareTo` metody.|  
|[DA0012: Vysoký objem odrazů](../profiling/da0012-significant-amount-of-reflection.md)|Volání <xref:System.Reflection?displayProperty=fullName> metody jako <xref:System.Reflection.IReflect.InvokeMember%2A> a <xref:System.Reflection.IReflect.GetMember%2A> nebo typ metody jako <xref:System.Type.InvokeMember%2A> jsou podstatnou část dat profilování. Pokud je to možné, zvažte nahrazení tyto metody s časná vazba metod závislá sestavení.|  
|[DA0013: Vysoké použití String.Split nebo String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Volání <xref:System.String.Split%2A?displayProperty=fullName> nebo <xref:System.String.Substring%2A> metody jsou podstatnou část dat profilování. Zvažte použití <xref:System.String.IndexOf%2A> nebo <xref:System.String.IndexOfAny%2A> Pokud testujete existenci podřetězce v řetězci.|  
|[DA0018: 32bitová aplikace spuštěná v limitech paměti spravovaného procesu](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Data systému, které jsou shromažďovány během profilování označuje, že rozhraní .NET Framework paměti haldy dosaženy maximální velikost, se kterým dosáhnete spravované haldy v 32bitový proces. Vezměte v úvahu profilaci znovu pomocí metody profilování paměti .NET a optimalizaci aplikací pomocí spravované prostředky.|  
|[DA0021: Vysoká míra 1. generace kolekce pamětí](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Relativně velké množství paměti objektů .NET jsou právě uvolněny v procesu uvolnění paměti generace 1. Pokud příliš mnoho krátkodobé objekty byly zachovány při shromažďování generace 0, náklady na správu paměti se snadno můžou stát nadměrné.|  
|[DA0022: Vysoká míra 2. generace kolekce pamětí](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Velké množství paměti objektů .NET jsou právě uvolněny v procesu uvolnění paměti generace 2. Pokud příliš mnoho krátkodobé objekty byly zachovány při 1. generace kolekce, náklady na správu paměti se snadno můžou stát nadměrné. Toto pravidlo je vyvoláno, když překročí vyšší prahová hodnota pravidla DA0005 míře sporů zámků.|  
|[DA0023: Vysoký čas procesoru uvolňování paměti](../profiling/da0023-high-gc-cpu-time.md)|Údaje o výkonu systému, který je shromážděných během profilace označuje, že množství času, který byl stráven uvolňování paměti je důležité ve srovnání s časem zpracování celkový počet aplikací.|  
|[DA0024: Nadměrný čas procesoru uvolňování paměti](../profiling/da0024-excessive-gc-cpu-time.md)|Údaje o výkonu systému, který je shromážděných během profilace označuje, že množství času, který byl stráven uvolňování paměti je příliš vysoká ve srovnání s časem zpracování celkový počet aplikací. Toto pravidlo je vyvoláno, když vyšší prahová hodnota pravidla DA0023 přesahuje množství času stráveného při uvolňování paměti.|  
|[DA0038: Vysoká míra kolizí zámků](../profiling/da0038-high-rate-of-lock-contentions.md)|Systém údaje o výkonu, která se shromažďují se data profilace označuje, že výrazně vysoké míře sporů zámků došlo k chybě při spuštění aplikace. Vezměte v úvahu profilaci znovu pomocí metody profilace souběžného zpracování najít příčinu sporů.|  
|[DA0039: Velmi vysoká míra kolizí zámků](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Systém údaje o výkonu, která se shromažďují se data profilace označuje, že došlo k příliš vysoké míře sporů zámků při spuštění aplikace. Vezměte v úvahu profilaci znovu pomocí metody profilace souběžného zpracování najít příčinu sporů. Toto pravidlo je vyvoláno, když překročí vyšší prahová hodnota pravidla DA0038 míře sporů zámků.|



