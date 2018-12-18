---
title: 'DA0005: Časté kolekce GC2 | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5e3038f873895e38cf162e67316bc08f2fc007b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849369"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Časté kolekce GC2

|||  
|-|-|  
|RuleId|DA0005|  
|Kategorie|Použití rozhraní .NET framework|  
|Metoda profilace|Paměť .NET|  
|Zpráva|Mnoho objektů je shromažďováno v uvolnění paměti generace 2.|  
|Typ zprávy|Upozornění|  

## <a name="cause"></a>příčina  
 Velké množství paměti objektů .NET jsou právě uvolněny v procesu uvolnění paměti generace 2.  

## <a name="rule-description"></a>Popis pravidla  
 Microsoft .NET common language runtime (CLR) poskytuje mechanismus správy automatické paměti, která používá systému uvolňování paměti pro uvolnění paměti z objektů, které aplikace se už používá. Uvolňování paměti je orientované na generování založeno na předpokladu, že jsou krátkodobé a jednorázové mnoho přidělení. Lokální proměnné by měl být například krátkodobou. Spustit nově vytvořené objekty v generaci 0 (0. generace) a potom pokroku na generaci 1, pokud se uvolňování paměti spusťte a nakonec přechod do 2. generace zvládnout situaci, kdy aplikace stále používá.  

 Objekty v generaci 0 se vybírají obvykle velmi efektivně a často. Objekty v 1. generace jsou shromažďovány méně často a méně efektivní. Nakonec dlouhodobými objekty v generaci 2 by měl být shromažďovány i méně často. 2. generace kolekce, která je spuštění úplného uvolňování paměti kolekce, je také nejvíce náročná operace.  

 Toto pravidlo je vyvoláno při proporcionálně příliš mnoho generace došlo k uvolnění paměti 2. Pokud moc relativně krátkodobé objekty byly zachovány při 1. generace kolekce, ale budou moct být shromážděny v celé kolekce generace 2, náklady na správu paměti se snadno můžou stát nadměrné. Další informace najdete v tématu [uprostřed života krize](http://go.microsoft.com/fwlink/?LinkId=177835) Zveřejněte na výkon Tidbits Rico Mariani na webové stránce MSDN.  

## <a name="how-to-investigate-a-warning"></a>Zkoumání upozornění  
 Zkontrolujte [zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md) sestav k pochopení způsobu přidělení paměti aplikace. Použití [zobrazení doby života objektu](../profiling/object-lifetime-view.md) pro určení, které programových datech objekty jsou zbývajících do 2. generace a potom uvolnit z něj. Použití [přidělení – zobrazení](../profiling/dotnet-memory-allocations-view.md) k určení postupu provádění, jejímž výsledkem těchto přidělení.  

 Informace o tom, jak zlepšit výkon kolekce uvolnění paměti, naleznete v tématu [základní informace o uvolňování paměti a typech výkonu](http://go.microsoft.com/fwlink/?LinkId=148226) na webu společnosti Microsoft. Informace o režii související se automatické uvolňování paměti naleznete v tématu [velký objekt haldy Nepokrytý](http://go.microsoft.com/fwlink/?LinkId=177836).