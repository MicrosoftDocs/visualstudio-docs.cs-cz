---
title: Profilace z příkazového řádku služby | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d8bffbaa2cf16c81d1d726043590c1b632560e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729851"
---
# <a name="command-line-profiling-of-services"></a>Profilace služeb z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato část popisuje postupy a možnosti pro shromažďování dat výkonu pro služby Windows s použitím [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástroje pro profilaci z příkazového řádku.  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Shromažďování statistik aplikace:** shromáždit statistiky výkonu pomocí metody odběru vzorků. Vzorkování dat je užitečné analyzovat problémy s využitím procesoru a pochopení charakteristik obecné informace o výkonu aplikace.|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Shromažďování podrobných dat časování:** pomocí metody instrumentace ke shromažďování podrobných informací o časování. Data instrumentace je užitečné pro analýzu problémů vstupně-výstupních operací a k podrobné analýze scénáře aplikací.|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Shromažďování dat paměti .NET:** pomocí vzorkování nebo instrumentace shromažďovat data o přidělování paměti .NET, který vám ukáže, velikost a počet přidělených objektů. Může také shromažďovat data o životním cyklu objektu, který vám ukáže, velikost a počet objektů, které jsou uvolněny v každé generaci uvolňování paměti.|-   [Shromažďování dat paměti .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Shromažďování dat souběžnosti:** můžete shromažďovat data kolize prostředků a data o činnosti vlákna, která ukazuje využití procesor, kolize vlákna, migrace vlákna, zpoždění synchronizace, oblastí překryté vstupně-výstupní operace a jiných za použití metody souběžnosti systémové události.|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
|**Přidání dat interakce vrstev:** přidáte údaje o výkonu o synchronní ADO.NET, který volá služby Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] databáze.|-   [Shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Související úlohy  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Profilovat samostatné (klientské) aplikace**|-   [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profil aplikace ASP.NET**|-   [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|



