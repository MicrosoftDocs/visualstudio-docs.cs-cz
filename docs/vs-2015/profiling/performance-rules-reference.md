---
title: Referenční informace o pravidlech výkonu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48659a0b5981d545a706abfcaa7c3db24052cd20
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548405"
---
# <a name="performance-rules-reference"></a>Referenční dokumentace pravidel výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pravidla výkonu Nástroje pro profilaci poskytují další upozornění a informace o výkonu aplikace. Pravidla výkonu analyzují data v běhu profilace, která se shromažďují ze zdrojů, jako jsou čítače výkonu Windows a procesoru. Zprávy pravidla se zobrazí v okně výstup chyby [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] integrovaného vývojového prostředí. Zprávy jsou uvedeny s jednou z následujících úrovní pravidel:  
  
|Kategorie|Popis|  
|-|-|  
|**Chyba**|Několik pravidel generuje chybové zprávy, protože většina problémů s výkonem není nesprávnými chybami. Chybová zpráva může indikovat selhání shromažďování dat profilování.|  
|**Upozornění**|Upozornění označují oblast vaší aplikace, která může být zdrojem problémů s výkonem nebo která může být výhodou optimalizace.|  
|**Informace**|Informační zprávy naznačují, že buď analýza podmínky pravidla nedosáhla prahové hodnoty pro vygenerování chybové zprávy, nebo že informace ve zprávě jsou užitečné, ale neodráží problém s výkonem.|  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Pravidla výkonu podle ID](../profiling/performance-rules-by-id.md)  
  
 Pravidla výkonu Nástroje pro profilaci jsou uspořádána ve čtyřech kategoriích:  
  
|Kategorie|Popis|  
|-|-|  
|[Pravidla výkonu .NET Framework využití](../profiling/dotnet-framework-usage-performance-rules.md)|Pravidla, která vám pomůžou efektivně používat .NET Framework.|  
|[Pravidla výkonu paměti a stránkování](../profiling/memory-and-paging-performance-rules.md)|Pravidla, která analyzují chování spravované paměti a stránkování vaší aplikace.|  
|[Nástroje pro profilaci pravidla použití](../profiling/profiling-tools-usage-rules.md)|Pravidla, která vám pomůžou efektivně používat Nástroje pro profilaci.|  
|[Pravidla výkonu monitorování prostředků](../profiling/resource-monitoring-performance-rules.md)|Informační zprávy o využití procesoru a paměti při spuštění profilace.|
