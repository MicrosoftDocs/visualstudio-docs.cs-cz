---
title: Command-Line profilování Stand-Alone aplikací | Microsoft Docs
description: Naučte se, jak pomocí Nástroje pro profilaci z příkazového řádku shromažďovat údaje o výkonu pro klientské aplikace (samostatné).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 876c2a72f0929cffa3613026fa56a17d82786854
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533638"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilace samostatných aplikací z příkazového řádku
Tato část popisuje postupy a možnosti pro shromažďování údajů o výkonu pro samostatné (klientské) aplikace pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci z příkazového řádku.

## <a name="common-tasks"></a>Běžné úkoly

| Úkol | Související obsah |
| - | - |
| **Shromáždit statistiku aplikace:** Ke shromažďování statistik výkonu použijte metodu vzorkování. Vzorkování dat je užitečné při analýze problémů s využitím procesoru a pro porozumění obecným vlastnostem výkonu aplikace. | -   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Shromažďování podrobných dat časování:** Použijte metodu instrumentace ke shromažďování podrobných informací o časování. Data instrumentace jsou užitečná pro analýzu problémů v/v a pro jemně odstupňovanou analýzu scénářů aplikací. | -   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Shromáždit data paměti .NET:** Pomocí vzorkování nebo instrumentace Shromážděte data o přidělování paměti .NET, která zobrazují velikost a počet přidělených objektů. Můžete také shromažďovat data o životnosti objektů, která zobrazují velikost a počet objektů, které jsou v každé generaci uvolňování paměti uvolněny. | -   [Shromažďování dat .NET Framework paměti](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Shromáždit data souběžnosti:** Použijte metodu souběžnosti ke shromáždění dat o kolize prostředku a data aktivity vláken, která vám ukáže využití procesoru, kolize vláken, migraci vláken, zpoždění synchronizace, oblasti překrývajících se vstupně-výstupních operací a další systémové události. | -   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Přidat data interakce vrstev:** Můžete přidat údaje o výkonu o synchronních voláních ADO.NET, která aplikace provedla v [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] databázi Microsoft. Přidání dat interakce vrstev do běhu profilování vyžaduje konkrétní procedury s nástroji pro profilaci příkazového řádku. | -   [Shromáždit data interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Související úlohy

|Úkol|Související obsah|
|----------|---------------------|
|**Profilování aplikací ASP.NET**|-   [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Profilovací služby**|-   [Profilovací služby](../profiling/command-line-profiling-of-services.md)|
