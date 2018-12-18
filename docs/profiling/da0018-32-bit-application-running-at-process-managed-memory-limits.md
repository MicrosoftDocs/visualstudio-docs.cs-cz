---
title: 'DA0018: 32bitová aplikace spuštěná v procesu limitech paměti spravovaného | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 013f4b0ed19a2227d6b86fe5fca2f8343d88f554
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921246"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018: 32bitová aplikace spuštěná v limitech paměti spravovaného procesu

|||  
|-|-|  
|Id pravidla|DA0018|  
|Kategorie|Použití nástroje pro profilaci|  
|Metoda profilace|Vzorkování|  
|Zpráva|Spravované přidělení paměti se blíží se limit počtu výchozí pro 32bitový proces. Vaše aplikace může být vázána na paměť.|  
|Typ pravidla|Upozornění|  

 Při profilování pomocí vzorkování, paměti .NET nebo metodám sporu prostředků, musíte shromáždit minimálně 10 vzorky k aktivaci tohoto pravidla.  

## <a name="cause"></a>příčina  
 Systém data shromážděná během spuštění profilování označuje, že rozhraní .NET Framework paměti haldy dosaženy maximální velikost, se kterým dosáhnete spravované haldy v 32bitový proces. Maximální velikost je výchozí hodnota. Je založen na celkové množství adresní prostor procesu je možné přidělit pro Nesdílené bajty. Hlášená hodnota je maximum pozorované hodnotu haldy zatímco byla aktivní profilovaný proces. Vezměte v úvahu profilaci znovu pomocí metody profilování paměti .NET a optimalizaci aplikací pomocí spravované prostředky.  

 Při velikosti spravované haldy přístup výchozí omezení, proces automatického uvolňování paměti kolekce pravděpodobně mají být vyvolány častěji. Tím se zvyšuje nároky na správu paměti.  

 Pravidlo je vyvoláno pouze pro 32bitové aplikace spuštěné na 32bitové počítače.  

## <a name="rule-description"></a>Popis pravidla  
 Rozhraní Microsoft .NET common language runtime (CLR) poskytuje mechanismus správy automatické paměti, která používá systému uvolňování paměti pro uvolnění paměti z objektů, které aplikace se už používá. Uvolňování paměti je orientované na generování založeno na předpokladu, že jsou krátkodobé a jednorázové mnoho přidělení. Lokální proměnné by měl být například krátkodobou. Spustit nově vytvořené objekty v generaci 0 (0. generace) a potom pokroku na generaci 1, pokud se uvolňování paměti spusťte a nakonec přechod do 2. generace zvládnout situaci, kdy aplikace stále používá.  

 Spravované objekty, které jsou větší než 85 KB přidělují na velkých objektových haldách, kde jsou v souladu s méně častým uvolňování paměti a komprimaci než menší objekty. velké objekty jsou spravovány samostatně, protože se předpokládá, že jsou více trvalé a protože kombinování trvalé a velké objekty se často přidělené objekty menší zapříčinit nejhorší přetypování fragmentaci haldě.  

 Celková velikost spravované haldy přístup výchozí omezení, nároky na správu paměti obvykle zvyšuje do bodu, kde můžete začít dopad na odezvu a škálovatelnost aplikace.  

## <a name="how-to-investigate-a-warning"></a>Zkoumání upozornění  
 Dvakrát klikněte na zprávu v okně Seznam chyb, přejděte [značky](../profiling/marks-view.md) zobrazení. Najít **paměť .NET CLR\\# bajtů ve všech haldách** a **# celkový počet zapsaných bajtů** sloupce. Zjistěte, jestli konkrétní fázích provádění programu kde je těžší než ostatní fáze přidělování spravované paměti. Porovnání hodnot **# bajtů ve všech haldách** ohlášení sloupec, který se frekvence uvolňování paměti **paměť .NET CLR\\Počet úklidů 0**, **paměť .NET CLR\\Počet úklidů 1**, a **paměť .NET CLR\\Počet úklidů 2** sloupce, abyste zjistili, pokud vzor přidělení spravované paměti ovlivňuje frekvence uvolňování paměti kolekce.  

 V aplikaci .NET Framework, modul common language runtime omezení celkové velikosti spravované haldy na o něco méně než polovinu maximální velikost části privátní oblast adresního prostoru procesu. 2 GB pro 32bitové procesy spuštěné na počítači 32-bit, představuje horní limit počtu privátních části adresního prostoru procesu. Celková velikost spravované haldy zahájení, abyste se jeho výchozí omezení, může se zvýšit nároky na správu paměti a může snížit výkon aplikace.  

 Pokud zatížení nadměrné spravované paměti je nějaký problém, vezměte v úvahu některé z těchto možností:  

- Optimalizace využití aplikace prostředků spravované paměti  

   -nebo-  

- kroků obdobná architektury omezení na maximální velikost virtuální paměti 32bitového procesu  

  Optimalizovat využití prostředků, spravované paměti aplikace, shromažďujte data o přidělování spravované paměti v běh profilování přidělení paměti .NET. Zkontrolujte [zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md) sestav k pochopení způsobu přidělení paměti aplikace.  

  Použití [zobrazení doby života objektu](../profiling/object-lifetime-view.md) pro určení, které programových datech objekty jsou zbývajících do generace a potom uvolnit z něj.  

  Použití [přidělení – zobrazení](../profiling/dotnet-memory-allocations-view.md) k určení postupu provádění, jejímž výsledkem těchto přidělení.  

  Další informace o tom, jak zlepšit výkon kolekce uvolnění paměti, naleznete v tématu rozhraní .NET Framework technického článku, [základní informace o uvolňování paměti a typech výkonu](http://go.microsoft.com/fwlink/?LinkId=177946) na webové stránce MSDN.  

  K získání architektury osvobození od omezení virtuální paměti na velikosti části privátní adresní prostor procesu, zkuste spustit tento 32bitový proces na 64bitovém počítači.  32bitový proces na 64bitovém počítači můžete získat až 4 GB přidělené virtuální paměti.  

  64-bit proces běží na 64bitovém počítači můžete získat až do 8 TB virtuální paměti. Vezměte v úvahu kompilací aplikace ke spuštění jako nativní 64bitové aplikace. Toto pravidlo je pouze pro informaci a nemusí potřebovat nápravné opatření.