---
title: Profilace z příkazového řádku služby | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87ebf5e363a85c90a7a546491e76044c0c8c1791
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813359"
---
# <a name="command-line-profiling-of-services"></a>Profilace služeb z příkazového řádku
Tato část popisuje postupy a možnosti pro shromažďování dat výkonu pro služby Windows s použitím [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroje pro profilaci z příkazového řádku.  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Běžné úlohy

  
| Úloha | Související obsah |
| - | - |
| **Shromažďování statistik aplikace:** shromáždit statistiky výkonu pomocí metody odběru vzorků. Vzorkování dat je užitečné analyzovat problémy s využitím procesoru a pochopení charakteristik obecné informace o výkonu aplikace. | -   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Shromažďování podrobných dat časování:** pomocí metody instrumentace ke shromažďování podrobných informací o časování. Data instrumentace je užitečné pro analýzu problémů vstupně-výstupních operací a k podrobné analýze scénáře aplikací. | -   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **Shromažďování dat paměti .NET:** pomocí vzorkování nebo instrumentace shromažďovat data o přidělování paměti .NET, který vám ukáže, velikost a počet přidělených objektů. Může také shromažďovat data o životním cyklu objektu, který vám ukáže, velikost a počet objektů, které jsou uvolněny v každé generaci uvolňování paměti. | -   [Shromažďování dat paměti .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Shromažďování dat souběžnosti:** můžete shromažďovat data kolize prostředků a data o činnosti vlákna, která ukazuje využití procesor, kolize vlákna, migrace vlákna, zpoždění synchronizace, oblastí překryté vstupně-výstupní operace a jiných za použití metody souběžnosti systémové události. | -   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Přidání dat interakce vrstev:** přidáte údaje o výkonu o synchronní ADO.NET, který volá služby Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] databáze. | -   [Shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
  
## <a name="related-tasks"></a>Související úlohy  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Profilovat samostatné (klientské) aplikace**|-   [Samostatné aplikace profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profil aplikace ASP.NET**|-   [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)|