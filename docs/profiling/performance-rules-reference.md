---
title: Referenční příručka pro pravidla výkonnosti | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772186"
---
# <a name="performance-rules-reference"></a>Referenční dokumentace pravidel výkonu
Pravidla výkonu nástroje profilování poskytují další upozornění a informace o výkonu aplikace. Pravidla výkonu analyzují data v profilovacím běhu, který je shromažďován ze zdrojů, jako je systém Windows a čítače výkonu procesoru. Zprávy pravidel se zobrazí v [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] okně Výstup chyby integrovaného vývojového prostředí. Zprávy jsou uvedeny s jednou z následujících úrovní pravidel:

|||
|-|-|
|**Chyba**|Několik pravidel generovat chybové zprávy, protože většina problémů s výkonem nejsou přímé chyby. Chybová zpráva může znamenat selhání shromažďování dat profilování.|
|**Upozornění**|Upozornění označují oblast aplikace, která může být potenciálně zdrojem problémů s výkonem nebo která může mít prospěch z optimalizace.|
|**Informace**|Informační zprávy označují, že buď analýza podmínky pravidla nedosáhla prahové hodnoty pro generování chybové zprávy, nebo že informace ve zprávě jsou užitečné, ale neodrážejí problém s výkonem.|

## <a name="in-this-section"></a>V tomto oddílu

[Pravidla výkonu podle identifikátorů](../profiling/performance-rules-by-id.md)

Pravidla výkonu Nástroje profilování jsou uspořádána do čtyř kategorií:

|||
|-|-|
|[Pravidla výkonu použití rozhraní .NET Framework](../profiling/dotnet-framework-usage-performance-rules.md)|Pravidla, která vám pomohou efektivně používat rozhraní .NET Framework.|
|[Pravidla výkonu paměti a stránkování](../profiling/memory-and-paging-performance-rules.md)|Pravidla, která analyzují spravované paměti a stránkování chování aplikace.|
|[Pravidla používání nástrojů pro profilaci](../profiling/profiling-tools-usage-rules.md)|Pravidla, která vám pomohou efektivně používat nástroje profilování.|
|[Pravidla výkonu sledování prostředků](../profiling/resource-monitoring-performance-rules.md)|Informační zprávy o využití procesoru a paměti v profilování spustit.|
