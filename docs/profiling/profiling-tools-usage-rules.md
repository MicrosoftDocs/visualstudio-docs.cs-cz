---
title: Pravidla používání nástrojů profilování | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 51c4f1384a58b19ad9a6a4f46ad0131158cc967c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778346"
---
# <a name="profiling-tools-usage-rules"></a>Pravidla používání nástrojů pro profilaci
Pravidla výkonu v kategorii Použití nástrojů profilování poskytují pokyny pro použití profileru k nejefektivnějšímu shromažďování dat.

| | |
| - | - |
| [DA0002: Chybí knihovna VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md) | Profilování příkazového řádku může obsahovat neúplná data pro binární soubory rozhraní .NET Framework. Příčinou může být nenastavíte správné proměnné prostředí. |
| [DA0003: Vysoký počet ukázek jádra](../profiling/da0003-many-kernel-samples.md) | Mnoho profilování vzorky, ke kterým došlo mimo provádění cílové binární byly zaznamenány. Chcete-li shromažďovat přesnější data, zvažte použití metody instrumentace. |
| [DA0004: Vysoké využití procesoru](../profiling/da0004-high-processor-usage.md) | Profilování data naznačují, že procesory byly konzistentně obsazeno během profilování spustit. Chcete-li shromáždit přesnější údaje, zvažte použití metody odběru vzorků. |
| [DA0008: Shromážděno málo ukázek](../profiling/da0008-few-samples-collected.md) | Počet vzorků odebraných při profilování nebyl dostatečně vysoký, aby byl statisticky významný. Zvažte profilování znovu a spuštění aplikace na delší dobu. Můžete také zvážit použití metody instrumentace ke shromažďování dat. |
| [DA0026: Nadměrný čas zpracování procesoru jádra](../profiling/da0026-excessive-kernel-cpu-time-processing.md) | V režimu jádra procesoru došlo k významnému množství času při profilování. Zvažte vzorkování pomocí systémových volání jako metriky namísto použití času jako metriky. |
| [DA0029: Nepodporovaná verze CLR](../profiling/da0029-unsupported-clr-version.md) | Profilovaný binární soubor používá verzi rozhraní .NET Framework, která není profilem podporována. Sestavy profileru nemohou přeložit názvy symbolů. |
| [DA0030: Získat Měření interakce vrstev pro databázové projekty](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md) | Byl shromážděn značný počet volání <xref:System.Data?displayProperty=fullName> metod v oboru názvů. Chcete-li zahrnout data o volání databáze, zvažte shromažďování dat interakce vrstvy ve vašem profilu spustí. |
