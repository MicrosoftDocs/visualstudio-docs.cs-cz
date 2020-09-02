---
title: Profilace samostatných aplikací z příkazového řádku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f4b2b78f7187b7a49b78312a1105a2af884fda3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186637"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilace samostatných aplikací z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato část popisuje postupy a možnosti pro shromažďování údajů o výkonu pro samostatné (klientské) aplikace pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci z příkazového řádku.  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|Úkol|Související obsah|  
|----------|---------------------|  
|**Shromáždit statistiku aplikace:** Ke shromažďování statistik výkonu použijte metodu vzorkování. Vzorkování dat je užitečné při analýze problémů s využitím procesoru a pro porozumění obecným vlastnostem výkonu aplikace.|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Shromažďování podrobných dat časování:** Použijte metodu instrumentace ke shromažďování podrobných informací o časování. Data instrumentace jsou užitečná pro analýzu problémů v/v a pro jemně odstupňovanou analýzu scénářů aplikací.|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Shromáždit data paměti .NET:** Pomocí vzorkování nebo instrumentace Shromážděte data o přidělování paměti .NET, která zobrazují velikost a počet přidělených objektů. Můžete také shromažďovat data o životnosti objektů, která zobrazují velikost a počet objektů, které jsou v každé generaci uvolňování paměti uvolněny.|-   [Shromažďování dat .NET Framework paměti](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Shromáždit data souběžnosti:** Použijte metodu souběžnosti ke shromáždění dat o kolize prostředku a data aktivity vláken, která vám ukáže využití procesoru, kolize vláken, migraci vláken, zpoždění synchronizace, oblasti překrývajících se vstupně-výstupních operací a další systémové události.|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Přidat data interakce vrstev:** Můžete přidat údaje o výkonu o synchronních voláních ADO.NET, která aplikace provedla v [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] databázi Microsoft. Přidání dat interakce vrstev do běhu profilování vyžaduje konkrétní procedury s nástroji pro profilaci příkazového řádku.|-   [Shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Vyzkoušet:** Pomocí podrobných kroků můžete profilovat ukázkovou klientskou aplikaci pomocí metody vzorkování nebo instrumentace.|-   [Návod: profilace z příkazového řádku s použitím vzorkování](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Návod: profilování z příkazového řádku pomocí instrumentace](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## <a name="related-tasks"></a>Související úlohy  
  
|Úkol|Související obsah|  
|----------|---------------------|  
|**Profilování aplikací ASP.NET**|-   [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**Profilovací služby**|-   [Služby profilace](../profiling/command-line-profiling-of-services.md)|
