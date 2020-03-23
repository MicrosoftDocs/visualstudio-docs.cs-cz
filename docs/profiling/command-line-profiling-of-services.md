---
title: Profilování služeb příkazového řádku | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: b20835eaf8b81bd64bd90aa75d2efb32975a7c53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772828"
---
# <a name="command-line-profiling-of-services"></a>Profilace služeb z příkazového řádku
Tato část popisuje postupy a možnosti pro shromažďování [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dat o výkonu pro služby systému Windows pomocí nástrojů profilování z příkazového řádku.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úkoly

| Úkol | Související obsah |
| - | - |
| **Shromažďujte statistiky aplikací:** Pomocí metody vzorkování shromažďujte statistiky výkonu. Vzorkování dat je užitečné pro analýzu problémů s využitím procesoru a pro pochopení obecných charakteristik výkonu aplikace. | -   [Shromažďujte statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Shromážděte podrobné údaje o časování:** Pomocí metody instrumentace shromažďovat podrobné informace o časování. Data instrumentace jsou užitečná pro analýzu problémů s vio a pro jemně odstupňovanou analýzu scénářů aplikací. | -   [Shromažďování podrobných časových dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **Shromažďujte data paměti .NET:** Vzorkování nebo instrumentace slouží ke shromažďování dat přidělení paměti .NET, která zobrazují velikost a počet přidělených objektů. Můžete také shromažďovat data životnosti objektu, který zobrazuje velikost a počet objektů, které jsou uvolněny v každé generování uvolňování paměti. | -   [Shromažďování dat paměti .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Shromažďovat data souběžnosti:** Pomocí metody souběžnosti shromažďujte data o konfliktu prostředků a data aktivity vláken, která zobrazují využití procesoru, konflikty vláken, migraci vláken, zpoždění synchronizace, oblasti překrývajících se vi a další systémové události. | -   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Přidejte data interakce vrstvy:** Můžete přidat údaje o výkonu synchronní ADO.NET volání, [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] která služba provedena do databáze společnosti Microsoft. | -   [Shromažďování dat interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Související úlohy

|Úkol|Související obsah|
|----------|---------------------|
|**Profilovat samostatné (klientské) aplikace**|-   [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profilové aplikace ASP.NET**|-   [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
