---
title: Command-Line profilování webových aplikací ASP.NET | Microsoft Docs
description: Naučte se, jak pomocí Nástroje pro profilaci z příkazového řádku shromažďovat údaje o výkonu pro webové aplikace v ASP.NET.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: c4c95890ae4022b854b76d2e4857fc2a27ce97e5
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533690"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilace webových aplikací ASP.NET z příkazového řádku
Tato část popisuje postupy a možnosti pro shromažďování údajů o výkonu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webových aplikací pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci z příkazového řádku.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úkoly

| Úkol | Související obsah |
| - | - |
| **Snadno Shromážděte základní data profilování ASP.NET:** Použijte nástroj **VSPerfASPNETCmd** ke shromažďování vzorkování, instrumentace, paměti .NET, kolizí nebo dat interakce vrstev bez požadavků na konfiguraci a restartování služby Internetová informační služba (IIS), které jsou potřeba pro **VSPerfCmd**. **VSPerfASPNETCmd** neumožňuje shromažďovat další data nebo řídit shromažďování dat. **Poznámka:**  **VSPerfASPNETCmd** je preferovaným nástrojem pro použití samostatného profileru k profilování ASP.NET webů. | -   [Rychlé profilování webu pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Shromáždit statistiku aplikace:** Ke shromažďování statistik výkonu použijte metodu vzorkování. Vzorkování dat je užitečné při analýze problémů s využitím procesoru a pro porozumění obecným vlastnostem výkonu aplikace. | -   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Shromažďování podrobných dat časování:** Použijte metodu instrumentace ke shromažďování podrobných informací o časování. Data instrumentace jsou užitečná při analýze vstupně-výstupních potíží a pro jemně odstupňovanou analýzu scénářů aplikací. | -   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **Shromáždit data paměti .NET:** Pomocí vzorkování nebo instrumentace Shromážděte data o přidělování paměti .NET, která zobrazují velikost a počet přidělených objektů. Můžete také shromažďovat data o životnosti objektů, která zobrazují velikost a počet objektů, které jsou v každé generaci uvolňování paměti uvolněny. | -   [Shromáždit data paměti](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Shromáždit data souběžnosti:** K shromažďování dat o kolizí prostředků použijte metodu souběžnosti. **Poznámka:**  Shromažďování dat aktivity vlákna a vizualizace není podporováno pro webové aplikace. | -   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Přidat data interakce vrstvy:** Můžete přidat údaje o výkonu o synchronních [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] voláních, která [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Webová aplikace provede v [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] databázi Microsoft. | -   [Shromáždit data interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Související úlohy

|Úkol|Související obsah|
|----------|---------------------|
|**Samostatné (klientské) aplikace profilu**|-   [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profilovací služby**|-   [Profilovací služby](../profiling/command-line-profiling-of-services.md)|
