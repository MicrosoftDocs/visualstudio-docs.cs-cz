---
title: Profilace samostatných aplikací z příkazového řádku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1def2cea8727502af32814d18c34ab36e27e3596
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938068"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilace samostatných aplikací z příkazového řádku
Tato část popisuje postupy a možnosti pro shromažďování dat výkonu pro samostatné (klientské) aplikace s použitím [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroje pro profilaci z příkazového řádku.  

## <a name="common-tasks"></a>Běžné úlohy  

| Úloha | Související obsah |
| - | - |
| **Shromažďování statistik aplikace:** shromáždit statistiky výkonu pomocí metody odběru vzorků. Vzorkování dat je užitečné analyzovat problémy s využitím procesoru a pochopení charakteristik obecné informace o výkonu aplikace. | -   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Shromažďování podrobných dat časování:** pomocí metody instrumentace ke shromažďování podrobných informací o časování. Data instrumentace je užitečná pro analýzu problémů vstupně-výstupních operací a k podrobné analýze scénáře aplikací. | -   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Shromažďování dat paměti .NET:** pomocí vzorkování nebo instrumentace shromažďovat data o přidělování paměti .NET, který vám ukáže, velikost a počet přidělených objektů. Může také shromažďovat data o životním cyklu objektu, který vám ukáže, velikost a počet objektů, které jsou uvolněny v každé generaci uvolňování paměti. | -   [Shromažďování dat paměti .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Shromažďování dat souběžnosti:** za použití metody souběžnosti můžete shromažďovat data kolize prostředků a data o činnosti vlákna, která ukazuje využití je využití procesoru, kolize vlákna, migrace vlákna, zpoždění synchronizace, oblasti překrytí vstupu-výstupu a dalších systémové události. | -   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Přidání dat interakce vrstev:** přidáte údaje o výkonu o synchronní ADO.NET, který volá žádosti na Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] databáze. Přidání dat interakce vrstvy do běhu profilování vyžaduje zvláštní procedury s nástroji pro profilaci příkazového řádku. | -   [Shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
| **Vyzkoušejte si to:** podrobné postupy použijte k ukázková klientská aplikace profilu pomocí metody vzorkování nebo instrumentace. | -   [Návod: Profilace z příkazového řádku pomocí vzorkování](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Návod: Profilace z příkazového řádku pomocí instrumentace](../profiling/walkthrough-command-line-profiling-using-instrumentation.md) |

## <a name="related-tasks"></a>Související úlohy  

|Úloha|Související obsah|  
|----------|---------------------|  
|**Profil aplikace ASP.NET**|-   [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**Profil služby**|-   [Profil služby](../profiling/command-line-profiling-of-services.md)|