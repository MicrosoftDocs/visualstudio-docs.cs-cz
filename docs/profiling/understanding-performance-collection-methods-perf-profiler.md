---
title: Porozumění metodám shromažďování informací o výkonu | Microsoft Docs
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: 03a49763a682f6b98b02fe40ba957efa8f5483c8
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290397"
---
# <a name="understand-performance-collection-methods"></a>Vysvětlení metod shromažďování výkonu

Tento dokument popisuje metody shromažďování dat, které využívají nástroje v profileru výkonu sady Visual Studio. 

## <a name="sampling"></a>Vzorkování

Metody vzorkování pro profilaci shromažďují statistická data o práci, kterou aplikace provádí během profilace. Shromažďování dat se provádí shromažďováním informací o aplikaci v pravidelných intervalech nebo vzorkovací četnosti, jako je například každých milisekund, a následnou analýzou těchto dat za účelem vytvoření modelu času stráveného v aplikaci. Metoda vzorkování je odlehčená a má malý vliv na spuštění aplikace, která je profilovaná. Nástroje v profileru výkonu, které využívají metodu vzorkování, zahrnují nástroj [využití CPU](../profiling/cpu-usage.md) .

## <a name="instrumentation"></a>Instrumentace

Profilace instrumentace shromažďuje podrobné informace o práci, kterou aplikace provádí při spuštění profilace. Shromažďování dat je provedeno pomocí nástrojů, které buď vloží kód do binárního souboru, který zachycuje informace o časování nebo pomocí zavěšení zpětného volání ke shromáždění a generování přesného časování a informací o počtu volání při spuštění aplikace. Metoda instrumentace má vysokou režii v porovnání s přístupy založenými na vzorkování. Nástroje v profileru výkonu, které používají instrumentaci, zahrnují Nástroj pro [přidělování objektů rozhraní .NET](../profiling/dotnet-alloc-tool.md) .