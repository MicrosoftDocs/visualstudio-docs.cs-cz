---
title: Profilace webových aplikací ASP.NET v příkazovém řádku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c93cb4774953f1425ff0330d7f588cbbf0f0b823
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64827446"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilace webových aplikací ASP.NET z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato část popisuje postupy a možnosti pro shromažďování údajů o výkonu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webových aplikací pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci z příkazového řádku.  
  
> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro Windows Store vyžadují také nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|Úkol|Související obsah|  
|----------|---------------------|  
|**Snadno Shromážděte základní data profilování ASP.NET:** Použijte nástroj **VSPerfASPNETCmd** ke shromažďování vzorkování, instrumentace, paměti .NET, kolizí nebo dat interakce vrstev bez požadavků na konfiguraci a restartování služby Internetová informační služba (IIS), které jsou potřeba pro **VSPerfCmd**. **VSPerfASPNETCmd** neumožňuje shromažďovat další data nebo řídit shromažďování dat. **Poznámka:**  **VSPerfASPNETCmd** je preferovaným nástrojem pro použití samostatného profileru k profilování ASP.NET webů.|-   [Rychlé profilování webu pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Shromáždit statistiku aplikace:** Ke shromažďování statistik výkonu použijte metodu vzorkování. Vzorkování dat je užitečné při analýze problémů s využitím procesoru a pro porozumění obecným vlastnostem výkonu aplikace.|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Shromažďování podrobných dat časování:** Použijte metodu instrumentace ke shromažďování podrobných informací o časování. Data instrumentace jsou užitečná při analýze vstupně-výstupních potíží a pro jemně odstupňovanou analýzu scénářů aplikací.|-   [Shromažďování podrobných dat časování pomocí instrumentace](/visualstudio/profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method?view=vs-2015)|  
|**Shromáždit data paměti .NET:** Pomocí vzorkování nebo instrumentace Shromážděte data o přidělování paměti .NET, která zobrazují velikost a počet přidělených objektů. Můžete také shromažďovat data o životnosti objektů, která zobrazují velikost a počet objektů, které jsou v každé generaci uvolňování paměti uvolněny.|-   [Shromažďování dat paměti](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Shromáždit data souběžnosti:** K shromažďování dat o kolizí prostředků použijte metodu souběžnosti. **Poznámka:**  Shromažďování dat aktivity vlákna a vizualizace není podporováno pro webové aplikace.|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Přidat data interakce vrstvy:** Můžete přidat údaje o výkonu o synchronních [!INCLUDE[vstecado](../includes/vstecado-md.md)] voláních, která [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Webová aplikace provede v [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] databázi Microsoft.|-   [Shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Související úlohy  
  
|Úkol|Související obsah|  
|----------|---------------------|  
|**Samostatné (klientské) aplikace profilu**|-   [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profilovací služby**|-   [Služby profilace](../profiling/command-line-profiling-of-services.md)|
