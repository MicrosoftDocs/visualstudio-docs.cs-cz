---
title: Profilování ASP.NET webových aplikací pomocí příkazového řádku | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: aa184667e5d569bc2662052a29b25bfea6e470a7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779568"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilování ASP.NET webových aplikací pomocí příkazového řádku
Tato část popisuje postupy a možnosti [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pro shromažďování [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dat o výkonu pro webové aplikace pomocí nástrojů profilování z příkazového řádku.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úkoly

| Úkol | Související obsah |
| - | - |
| **Snadno shromažďujte základní data ASP.NET profilování:** Pomocí nástroje **VSPerfASPNETCmd** můžete shromažďovat vzorkování, instrumentaci, paměť .NET, sváry nebo data interakce vrstvy bez požadavků na konfiguraci a restartování Internetové informační služby (IIS), které jsou potřebné pro **vsperfcmd**. **VSPerfASPNETCmd** neumožňuje shromažďovat další data nebo řídit shromažďování dat. **Poznámka:**  **VSPerfASPNETCmd** je upřednostňovaný nástroj pro použití samostatného profileru k profilování ASP.NET webových stránek. | -   [Rychlé profilování webových stránek s VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Shromažďujte statistiky aplikací:** Pomocí metody vzorkování shromažďujte statistiky výkonu. Vzorkování dat je užitečné pro analýzu problémů s využitím procesoru a pro pochopení obecných charakteristik výkonu aplikace. | -   [Shromažďujte statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Shromážděte podrobné údaje o časování:** Pomocí metody instrumentace shromažďovat podrobné informace o časování. Data instrumentace jsou užitečná pro analýzu problémů s vio a pro jemně odstupňovanou analýzu scénářů aplikací. | -   [Shromažďování podrobných časových dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **Shromažďujte data paměti .NET:** Vzorkování nebo instrumentace slouží ke shromažďování dat přidělení paměti .NET, která zobrazují velikost a počet přidělených objektů. Můžete také shromažďovat data životnosti objektu, který zobrazuje velikost a počet objektů, které jsou uvolněny v každé generování uvolňování paměti. | -   [Shromažďování paměťových dat](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Shromažďovat data souběžnosti:** Pomocí metody souběžnosti shromažďujte data tvrzení o prostředcích. **Poznámka:**  Shromažďování aktivit y vlákna a dat vizualizace není pro webové aplikace podporováno. | -   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Přidejte data interakce vrstvy:** Do databáze společnosti Microsoft [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] můžete přidat údaje o výkonu synchronních volání, která webová aplikace provádí. | -   [Shromažďování dat interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Související úlohy

|Úkol|Související obsah|
|----------|---------------------|
|**Profilovat samostatné (klientské) aplikace**|-   [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profilové služby**|-   [Profilové služby](../profiling/command-line-profiling-of-services.md)|
