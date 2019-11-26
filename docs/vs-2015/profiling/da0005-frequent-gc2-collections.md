---
title: 'DA0005: časté kolekce shromažďování gc2 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce96be60126f5693bfb4ba504a756e0ce76b0b2d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301249"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Časté shromažďování GC2
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

RuleId | DA0005 |  
| Kategorie |. Použití rozhraní .NET Framework |  
| Metoda profilování |. Paměť v síti |  
| Zpráva | Mnohé z vašich objektů se shromažďují v paměti generace 2. |  
| Typ zprávy | Upozornění |  
  
## <a name="cause"></a>Příčina  
 V uvolňování paměti 2. generace se uvolňuje velký počet paměťových objektů .NET.  
  
## <a name="rule-description"></a>Popis pravidla  
 Modul CLR (Common Language Runtime) Microsoft .NET poskytuje automatický mechanismus správy paměti, který používá systém uvolňování paměti k uvolnění paměti z objektů, které už aplikace nepoužívá. Systém uvolňování paměti je zaměřený na generaci, a to na základě předpokladu, že mnoho přidělení je krátkodobé. Místní proměnné, například by měly být krátkodobé. Nově vytvořené objekty začínají v generaci 0 (gen 0) a poté budou dokončeny na generaci 1, když přestanou běžet v uvolňování paměti, a nakonec přechod na generaci 2, pokud je aplikace stále používá.  
  
 Objekty v generaci 0 jsou často shromažďovány a obvykle velmi efektivně. Objekty v generaci 1 jsou shromažďovány méně často a méně efektivní. A konečně dlouhodobé objekty v generaci 2 by měly být shromažďovány ještě méně často. Největší náročná operace je shromažďování 2, což je úplné spuštění uvolňování paměti.  
  
 Toto pravidlo je vyvoláno, když došlo k proporcování příliš velkého počtu uvolnění paměti generace 2. Pokud je v kolekci 1. generace načteno příliš mnoho poměrně krátkodobých objektů, ale je možné je shromáždit v úplné kolekci 2. generace, náklady na správu paměti lze snadno přetvořit. Další informace najdete v části věnované [krizi v polovině životního cyklu](https://go.microsoft.com/fwlink/?LinkId=177835) na webu MSDN na Mariani výkonu pikantní.  
  
## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění  
 Projděte si sestavy [zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md) , abyste pochopili, jaký je model přidělení paměti aplikace. Pomocí [zobrazení životnosti objektů](../profiling/object-lifetime-view.md) určete, který z datových objektů programu je v generaci 2, a pak se z něj uvolní. Pomocí [zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md) Určete cestu spuštění, která je výsledkem těchto přidělení.  
  
 Informace o tom, jak zlepšit výkon uvolňování paměti, najdete v tématu [základy systému uvolňování paměti a Nápověda ke zvýšení výkonu](https://go.microsoft.com/fwlink/?LinkId=148226) na webu společnosti Microsoft. Informace o režii automatického uvolňování paměti najdete v tématu [large object halda se nepokryla](https://go.microsoft.com/fwlink/?LinkId=177836).
