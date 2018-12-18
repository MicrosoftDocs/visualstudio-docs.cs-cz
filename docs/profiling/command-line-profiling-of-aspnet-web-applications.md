---
title: Profilace webových aplikací ASP.NET z příkazového řádku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 03cb8a6b28ed5f5fece49644d9b1df2608f3e36d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895662"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilace z příkazového řádku z webové aplikace ASP.NET
Tato část popisuje postupy a možnosti pro shromažďování dat výkonu pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace s použitím [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroje pro profilaci z příkazového řádku.  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Běžné úlohy
  
| Úloha | Související obsah |
| - | - |
| **Shromažďování dat profilování snadno základní ASP.NET:** použití **VSPerfASPNETCmd** nástroj pro shromažďování vzorkování, instrumentace, paměti .NET, kolize nebo vrstvy interakce dat bez potřeby jejich požadavky na konfiguraci a Restartování Internetové informační služby (IIS), které jsou potřebné pro **VSPerfCmd**. **Příkaz VSPerfASPNETCmd** neumožňuje pro shromažďování dalších dat nebo pro sběr dat řídit. **Poznámka:****VSPerfASPNETCmd** je preferovaný nástroj použít, můžete použít samostatný profiler k profilu ASP.NET Web sites. | -   [Pohotová profilace stránek pomocí VSPerfASPNETCmd webových](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Shromažďování statistik aplikace:** shromáždit statistiky výkonu pomocí metody odběru vzorků. Vzorkování dat je užitečný pro analýzu využití problémy s Procesorem a pochopení charakteristik obecné informace o výkonu aplikace. | -   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Shromažďování podrobných dat časování:** pomocí metody instrumentace ke shromažďování podrobných informací o časování. Data instrumentace je užitečné pro analýzu problémů vstupně-výstupních operací a k podrobné analýze scénáře aplikací. | -   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **Shromažďování dat paměti .NET:** pomocí vzorkování nebo instrumentace shromažďovat data o přidělování paměti .NET, který vám ukáže, velikost a počet přidělených objektů. Může také shromažďovat data o životním cyklu objektu, který vám ukáže, velikost a počet objektů, které jsou uvolněny v každé generaci uvolňování paměti. | -   [Shromažďování dat paměti](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Shromažďování dat souběžnosti:** za použití metody souběžnosti můžete shromažďovat data kolize prostředků. **Poznámka:** shromažďování vlákno aktivity a vizualizace dat se nepodporuje pro webové aplikace. | -   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Přidání dat interakce vrstev:** můžete přidat data o výkonu o synchronních [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] volání [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webová aplikace odešle společnosti Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] databáze. | -   [Shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
  
## <a name="related-tasks"></a>Související úlohy

  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Profilovat samostatné (klientské) aplikace**|-   [Samostatné aplikace profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profil služby**|-   [Profil služby](../profiling/command-line-profiling-of-services.md)|