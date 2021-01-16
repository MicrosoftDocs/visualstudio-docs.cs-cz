---
title: Command-Line profilování služeb | Microsoft Docs
description: Naučte se, jak pomocí Nástroje pro profilaci z příkazového řádku shromažďovat data o výkonu pro služby systému Windows.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f05ca0a11060e2a9009b38b0caf7ce9172773f36
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533651"
---
# <a name="command-line-profiling-of-services"></a>Profilace služeb z příkazového řádku
Tato část popisuje postupy a možnosti pro shromažďování údajů o výkonu pro služby systému Windows pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci z příkazového řádku.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úkoly

| Úkol | Související obsah |
| - | - |
| **Shromáždit statistiku aplikace:** Ke shromažďování statistik výkonu použijte metodu vzorkování. Vzorkování dat je užitečné při analýze problémů s využitím procesoru a pro porozumění obecným vlastnostem výkonu aplikace. | -   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Shromažďování podrobných dat časování:** Použijte metodu instrumentace ke shromažďování podrobných informací o časování. Data instrumentace jsou užitečná při analýze vstupně-výstupních potíží a pro jemně odstupňovanou analýzu scénářů aplikací. | -   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **Shromáždit data paměti .NET:** Pomocí vzorkování nebo instrumentace Shromážděte data o přidělování paměti .NET, která zobrazují velikost a počet přidělených objektů. Můžete také shromažďovat data o životnosti objektů, která zobrazují velikost a počet objektů, které jsou v každé generaci uvolňování paměti uvolněny. | -   [Shromažďovat data paměti .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Shromáždit data souběžnosti:** Použijte metodu souběžnosti ke shromáždění dat o kolize prostředku a data aktivity vláken, která vám poukazují využití procesoru, kolize vláken, migraci vláken, zpoždění synchronizace, oblasti překrývajících se vstupně-výstupní operace a další systémové události. | -   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Přidat data interakce vrstvy:** Můžete přidat údaje o výkonu o synchronních voláních ADO.NET, která služba provedla v [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] databázi Microsoft. | -   [Shromáždit data interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Související úlohy

|Úkol|Související obsah|
|----------|---------------------|
|**Samostatné (klientské) aplikace profilu**|-   [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profilování aplikací ASP.NET**|-   [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
