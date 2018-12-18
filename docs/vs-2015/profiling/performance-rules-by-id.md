---
title: Pravidla výkonu podle identifikátorů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a1c934c-4798-4df9-a8ef-eb17ef06b6a2
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b78e586bdc2859364097fc03bfe4a667a481680e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737794"
---
# <a name="performance-rules-by-id"></a>Pravidla výkonu podle identifikátorů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upozornění|Popis|  
|-------------|-----------------|  
|[DA0001: Pro řetězení používejte StringBuilder](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Volání System.String.Concat jsou podstatnou část dat profilování. Zvažte použití <xref:System.Text.StringBuilder> třídy k vytvoření řetězce z více segmentů.|  
|[DA0002: Chybí knihovna VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|Profileru nelze najít VSPerfCorProf.dll během spuštění profilování. K tomuto upozornění dochází, bez použití nástroje VSPerfCLREnv.cmd inicializovat nezbytné proměnné prostředí se zadáním příkazového řádku nástrojů pro shromažďování dat profileru.|  
|[DA0003: Vysoký počet ukázek jádra](../profiling/da0003-many-kernel-samples.md)|Podstatnou část ukázky zásobníku volání shromážděných pro aplikaci se spouští v režimu jádra. Zvažte profilaci vaší aplikace pomocí jiné metody profilace.|  
|[DA0004: Vysoké využití procesoru](../profiling/da0004-high-processor-usage.md)|Využití procesoru (CPU) bylo velmi vysokou v profilaci dat, která byla shromážděna pomocí metody instrumentace. Zvažte použití při profilování Procesorem vázán aplikace metoda profilování vzorkování.|  
|[DA0005: Časté kolekce GC2](../profiling/da0005-frequent-gc2-collections.md)|Velké množství paměti objektů .NET jsou právě uvolněny v procesu uvolnění paměti generace 2.|  
|[DA0006: Přepište Equals() pro hodnoty](../profiling/da0006-override-equals-parens-for-value-types.md)|Volání metody Equals a operátory rovnosti veřejné hodnotového typu je podstatnou část dat profilování. Zvažte implementaci metodu efektivnější.|  
|[DA0007: Vyhněte se použití výjimek pro tok řízení](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Vysoký počet obslužných rutin výjimek rozhraní .NET Framework byly volány v dat profilování. Zvažte použití další logiku toku řízení k omezení počtu výjimek, které jsou vyvolány.|  
|[DA0008: Shromážděno málo ukázek](../profiling/da0008-few-samples-collected.md)|Pouze několik ukázky byly shromážděny během spuštění profilování. Zvažte delší spuštění nebo rychlejší vzorkovací frekvenci pro více významné výsledky.|  
|[DA0009: Vysoké hodnoty % času v překladu za běhu](http://msdn.microsoft.com/en-us/b60c1767-515c-41d9-81c2-c70d0b7024fd)|Významného procenta času spuštění aplikace se využilo na kompilátoru právě In Time (JIT).|  
|[DA0010: Náročná metoda GetHashCode](../profiling/da0010-expensive-gethashcode.md)|Volání metody GetHashCode typu jsou podstatnou část dat profilování nebo metodu přidělí paměť.|  
|[DA0011: Náročná metoda CompareTo](../profiling/da0011-expensive-compareto.md)|Metoda CompareTo typu je nákladné nebo přidělí paměť.|  
|[DA0012: Vysoký objem odrazů](../profiling/da0012-significant-amount-of-reflection.md)|Volání metody System.Reflection například metodu InvokeMember a GetMember nebo typ metody, jako je například MemberInvoke je podstatnou část dat profilování. Pokud je to možné, zvažte nahrazení tyto metody s časná vazba metod závislá sestavení.|  
|[DA0013: Vysoké použití String.Split nebo String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Volání metody System.String.Split nebo System.String.Substring jsou signifiicant část dat profilování. Zvažte použití System.String.IndexOf nebo System.String.IndexOfAny Pokud testujete existenci podřetězce v řetězci.|  
|[DA0014: Velmi vysoké míry stránkování aktivní paměti na disk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Údaje o výkonu systému, která byla shromážděna během profilování označuje, že k velmi vysokým mírám stránkování aktivní paměti na a z disku došlo k chybě během spuštění profilování. Stránkování sazby na této úrovni obvykle ovlivní výkon aplikace a rychlost odezvy. Zvažte snížení přidělení paměti prostřednictvím revize algoritmy. Budete také muset zvážit požadavky na paměť vaší aplikace. spuštění v počítači, který má více paměti pro profilaci znovu.|  
|[DA0017: Vysoké míry stránkování aktivní paměti na disk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Údaje o výkonu systému, která byla shromážděna během profilování označuje, že vysokým mírám stránkování aktivní paměti na a z disku došlo k chybě během spuštění profilování. Stránkování sazby na této úrovni obvykle ovlivní výkon aplikace a rychlost odezvy. Zvažte snížení přidělení paměti prostřednictvím revize algoritmy. Budete také muset zvážit požadavky na paměť vaší aplikace. spuštění v počítači, který má více paměti pro profilaci znovu.|  
|[DA0018: 32bitová aplikace spuštěná v limitech paměti spravovaného procesu](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Data systému, která byla shromážděna během profilování označuje, že rozhraní .NET Framework paměti haldy dosaženy maximální velikosti spravované haldy růst, aby v 32bitový proces. Hlášená hodnota je maximum pozorované hodnotu haldy při se profilovaný proces byl aktivní. Uvažujte o optimalizaci aplikací pomocí spravované prostředky.|  
|[DA0021: Vysoká míra 1. generace kolekce pamětí](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Údaje o výkonu systému, která byla shromážděna během profilování znamenat, že podstatnou část objekty paměti for.NET Framework byla uvolněny v 1. generace uvolňování ve srovnání s shromažďování dat 0. generace.|  
|[DA0022: Vysoká míra 2. generace kolekce pamětí](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Údaje o výkonu systému, která byla shromážděna během profilování znamenat, že podstatnou část objekty paměti for.NET Framework byla uvolněny v procesu 2. generace uvolňování paměti ve srovnání s 0. generace a uvolnění paměti generace 1.|  
|[DA0023: Vysoký čas procesoru uvolňování paměti](../profiling/da0023-high-gc-cpu-time.md)|Údaje o výkonu systému, která byla shromážděna během profilování označuje, že množství času stráveného při uvolňování paměti je důležité ve srovnání s časem zpracování celkový počet aplikací.|  
|[DA0024: Nadměrný čas procesoru uvolňování paměti](../profiling/da0024-excessive-gc-cpu-time.md)|Údaje o výkonu systému, která byla shromážděna během profilování označuje, že množství času stráveného při uvolňování paměti je příliš vysoká ve srovnání s časem zpracování celkový počet aplikací.|  
|[DA0026: Nadměrný čas zpracování procesoru jádra](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|Čas procesoru poměr, který se spustil v režimu jádra překročil množství času strávené v uživatelském režimu. Zvažte profilaci znovu a vzorkování počet volání systému (syscalls) a zjistěte příčinu časy spuštění režimu jádra vysoká.|  
|[DA0029: Nepodporovaná verze CLR](../profiling/da0029-unsupported-clr-version.md)|Pokoušíte se Profilovat aplikaci, která používá rozhraní .NET Framework verze 1.1, která není podporována v nástrojích pro profilaci.|  
|[DA0030: Získat Měření interakce vrstev pro databázové projekty](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Volání <xref:System.Data> podstatnou část dat profilování jsou metody a nebyly shromážděných dat interakce vrstev při spuštění profilace. Zvažte profilaci znovu a přidání dat interakce vrstev.|  
|[DA0038: Vysoká míra kolizí zámků](../profiling/da0038-high-rate-of-lock-contentions.md)|Systém údaje o výkonu, která se shromažďují se data profilace označuje, že výrazně vysoké míře sporů zámků došlo k chybě při spuštění aplikace. Vezměte v úvahu profilaci znovu pomocí metody profilace souběžného zpracování najít příčinu sporů.|  
|[DA0039: Velmi vysoká míra kolizí zámků](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Systém údaje o výkonu, která se shromažďují se data profilace označuje, že došlo k příliš vysoké míře sporů zámků při spuštění aplikace. Vezměte v úvahu profilaci znovu pomocí metody profilace souběžného zpracování najít příčinu spory.|  
|[DA0501: Průměr spotřeby procesoru profilovaným procesem](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Tato zpráva znamená procentuální hodnotu času, který byl procesor zaneprázdněný, provádění instrukcí z aplikace. Hlášená hodnota je průměrem přes všechny intervaly měření, ve kterých byl aktivní profilovaný proces. Hodnota může být větší než 100 % na počítači s více než jeden procesor.|  
|[DA0502: Maximum spotřeby procesoru profilovaným procesem](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Tato zpráva znamená maximální procento času, který byl procesor zaneprázdněný, provádění instrukcí z aplikace. Hlášená hodnota je maximální hodnota uvedená mezi všechny intervaly měření, ve kterých byl aktivní profilovaný proces. Procento, může být větší než 100 % na počítači s více než jeden procesor.|  
|[DA0503: Průměr pracovní sady v bajtech pro profilovaný proces](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Tato zpráva znamená Průměrná velikost fyzické paměti, který právě používá procesu v bajtech (pracovní sady). Pracovní sada procesu představuje stránek z adresního prostoru procesu, která jsou aktuálně umístěny ve fyzické paměti.|  
|[DA0504: Maximum pracovní sady v bajtech pro profilovaný proces](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Tato zpráva znamená maximální velikost fyzické paměti, který právě používá procesu v bajtech. Pracovní sada procesu představuje stránek z adresního prostoru procesu, která jsou aktuálně umístěny ve fyzické paměti. Toto pravidlo sestavy maximální hodnota pracovní sady procesu během profilace byl aktivní.|  
|[DA0505: Průměr nesdílených bajtů přidělených pro profilovaný proces](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Tato zpráva znamená Průměrná velikost virtuální paměti, který má proces nyní přidělenu v bajtech (Nesdílené bajty). Nesdílené bajty představuje virtuální paměti umístění, které byly přiděleny procesem, který je přístupný pouze tím, že běží uvnitř procesu vlákna.|  
|[DA0506: Maximum nesdílených bajtů přidělených pro profilovaný proces](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Tato zpráva znamená maximální velikost virtuální paměti, který má proces nyní přidělenu v bajtech (Nesdílené bajty). Nesdílené bajty představuje virtuální paměti umístění, které byly přiděleny procesem, který je přístupný pouze tím, že běží uvnitř procesu vlákna.|



