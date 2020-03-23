---
title: Profilování samostatných aplikací příkazového řádku | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 3f80f3e65969973202af08299b07ebfa420f3bd2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77557852"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilace samostatných aplikací z příkazového řádku
Tato část popisuje postupy a možnosti pro shromažďování dat o výkonu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pro samostatné (klientské) aplikace pomocí nástrojů profilování z příkazového řádku.

## <a name="common-tasks"></a>Běžné úkoly

| Úkol | Související obsah |
| - | - |
| **Shromažďujte statistiky aplikací:** Pomocí metody vzorkování shromažďujte statistiky výkonu. Vzorkování dat je užitečné pro analýzu problémů s využitím procesoru a pro pochopení obecných charakteristik výkonu aplikace. | -   [Shromažďujte statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Shromážděte podrobné údaje o časování:** Pomocí metody instrumentace shromažďovat podrobné informace o časování. Data instrumentace jsou užitečná pro analýzu vstupně-va problémů a pro jemně odstupňovanou analýzu scénářů aplikací. | -   [Shromažďování podrobných časových dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Shromažďujte data paměti .NET:** Vzorkování nebo instrumentace slouží ke shromažďování dat přidělení paměti .NET, která zobrazují velikost a počet přidělených objektů. Můžete také shromažďovat data životnosti objektu, který zobrazuje velikost a počet objektů, které jsou uvolněny v každé generování uvolňování paměti. | -   [Shromažďování paměťových dat rozhraní .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Shromažďovat data souběžnosti:** Pomocí metody souběžnosti můžete shromažďovat data o konfliktu prostředků a data o aktivitě vláken, která zobrazují využití procesoru, konflikty vláken, migraci vláken, zpoždění synchronizace, oblasti překrývajících se vstupně-va a dalších systémových událostí. | -   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Přidejte data interakce na úrovni:** Můžete přidat údaje o výkonu synchronní ADO.NET volání, [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] která aplikace provedena do databáze společnosti Microsoft. Přidání dat interakce vrstvy do spuštění profilování vyžaduje specifické postupy s nástroji profilování příkazového řádku. | -   [Shromažďování dat interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Související úlohy

|Úkol|Související obsah|
|----------|---------------------|
|**Profilové aplikace ASP.NET**|-   [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Profilové služby**|-   [Profilové služby](../profiling/command-line-profiling-of-services.md)|
