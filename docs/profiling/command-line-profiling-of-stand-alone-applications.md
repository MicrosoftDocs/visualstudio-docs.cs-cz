---
title: Profilace samostatných aplikací z příkazového řádku | Microsoft Docs
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
ms.openlocfilehash: c5fd11f12f368c266dd19577925db7cec1867e39
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779542"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilace samostatných aplikací z příkazového řádku
Tato část popisuje postupy a možnosti pro shromažďování údajů o výkonu pro samostatné (klientské) aplikace pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci z příkazového řádku.

## <a name="common-tasks"></a>Běžné úlohy

| Úloha | Související obsah |
| - | - |
| **Shromáždit statistiku aplikace:** Ke shromažďování statistik výkonu použijte metodu vzorkování. Vzorkování dat je užitečné při analýze problémů s využitím procesoru a pro porozumění obecným vlastnostem výkonu aplikace. | -   [shromažďovat statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Shromažďování podrobných dat časování:** Použijte metodu instrumentace ke shromažďování podrobných informací o časování. Data instrumentace jsou užitečná pro analýzu problémů v/v a pro jemně odstupňovanou analýzu scénářů aplikací. | -   [shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Shromáždit data paměti .NET:** Pomocí vzorkování nebo instrumentace Shromážděte data o přidělování paměti .NET, která zobrazují velikost a počet přidělených objektů. Můžete také shromažďovat data o životnosti objektů, která zobrazují velikost a počet objektů, které jsou v každé generaci uvolňování paměti uvolněny. | -   [shromažďovat data o .NET Framework paměti](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Shromáždit data souběžnosti:** Použijte metodu souběžnosti ke shromáždění dat o kolize prostředku a data aktivity vláken, která vám ukáže využití procesoru, kolize vláken, migraci vláken, zpoždění synchronizace, oblasti překrývajících se vstupně-výstupních operací a další systémové události. | -   [shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Přidat data interakce vrstev:** Můžete přidat údaje o výkonu o synchronních voláních ADO.NET, která aplikace provedla v databázi Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. Přidání dat interakce vrstev do běhu profilování vyžaduje konkrétní procedury s nástroji pro profilaci příkazového řádku. | -   [shromažďovat data interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
| **Vyzkoušet:** Pomocí podrobných kroků můžete profilovat ukázkovou klientskou aplikaci pomocí metody vzorkování nebo instrumentace. | -   [Návod: profilace z příkazového řádku s použitím vzorkování](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Návod: profilování z příkazového řádku pomocí instrumentace](command-line-profiling-of-stand-alone-applications.md) |

## <a name="related-tasks"></a>Související úlohy

|Úloha|Související obsah|
|----------|---------------------|
|**Profilování aplikací ASP.NET**|[webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md) -   |
|**Profilovací služby**|[služby profilů](../profiling/command-line-profiling-of-services.md) -   |
