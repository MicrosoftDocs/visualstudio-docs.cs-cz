---
title: Referenční informace o pravidlech výkonu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 446e47f50c81fa5bad979117936faef53ad3ef63
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74772186"
---
# <a name="performance-rules-reference"></a>Referenční dokumentace pravidel výkonu
Pravidla výkonu Nástroje pro profilaci poskytují další upozornění a informace o výkonu aplikace. Pravidla výkonu analyzují data v běhu profilace, která se shromažďují ze zdrojů, jako jsou čítače výkonu Windows a procesoru. Zprávy pravidla se zobrazí v okně výstup chyby v integrovaném vývojovém prostředí [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Zprávy jsou uvedeny s jednou z následujících úrovní pravidel:

|||
|-|-|
|**Chyba**|Několik pravidel generuje chybové zprávy, protože většina problémů s výkonem není nesprávnými chybami. Chybová zpráva může indikovat selhání shromažďování dat profilování.|
|**Upozornění**|Upozornění označují oblast vaší aplikace, která může být zdrojem problémů s výkonem nebo která může být výhodou optimalizace.|
|**Informace**|Informační zprávy naznačují, že buď analýza podmínky pravidla nedosáhla prahové hodnoty pro vygenerování chybové zprávy, nebo že informace ve zprávě jsou užitečné, ale neodráží problém s výkonem.|

## <a name="in-this-section"></a>V tomto oddílu

[Pravidla výkonu podle identifikátorů](../profiling/performance-rules-by-id.md)

Pravidla výkonu Nástroje pro profilaci jsou uspořádána ve čtyřech kategoriích:

|||
|-|-|
|[Pravidla výkonu použití rozhraní .NET Framework](../profiling/dotnet-framework-usage-performance-rules.md)|Pravidla, která vám pomůžou efektivně používat .NET Framework.|
|[Pravidla výkonu paměti a stránkování](../profiling/memory-and-paging-performance-rules.md)|Pravidla, která analyzují chování spravované paměti a stránkování vaší aplikace.|
|[Pravidla používání nástrojů pro profilaci](../profiling/profiling-tools-usage-rules.md)|Pravidla, která vám pomůžou efektivně používat Nástroje pro profilaci.|
|[Pravidla výkonu sledování prostředků](../profiling/resource-monitoring-performance-rules.md)|Informační zprávy o využití procesoru a paměti při spuštění profilace.|
