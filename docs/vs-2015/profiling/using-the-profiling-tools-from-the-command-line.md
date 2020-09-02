---
title: Použití Nástroje pro profilaci z příkazového řádku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ebd0fbabb73d4c77d1d888b207882e7403f46aab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64822686"
---
# <a name="using-the-profiling-tools-from-the-command-line"></a>Použití nástrojů pro profilaci z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí nástrojů příkazového řádku [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci můžete Profilovat aplikace na příkazovém řádku a automatizovat profilaci pomocí dávkových souborů a skriptování. Soubory sestav můžete také vygenerovat na příkazovém řádku. Pomocí zjednodušeného samostatného profileru můžete shromažďovat data na počítačích, které nejsou [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nainstalované.  
  
> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro Windows Store vyžadují také nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|Úkol|Související obsah|  
|----------|---------------------|  
|**Nastavte umístění symbolů:** Pro zobrazení názvů funkcí a parametrů musí mít Profiler přístup k souborům symbolů (. pdb) profilované binární soubory. Tyto soubory by měly obsahovat soubory symbolů pro operační systém a aplikace společnosti Microsoft, které chcete zobrazit ve vaší analýze. Pomocí veřejného serveru Microsoft symbol server se ujistěte, že máte správné soubory. PDB pro binární soubory společnosti Microsoft.|-   [Postupy: určení umístění souborů symbolů z příkazového řádku](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Profilování aplikace:** Nástroje příkazového řádku a možnosti, které slouží k profilování cílové aplikace, závisí na typu aplikace, metodě profilování a na tom, zda je cílem spravovaná nebo nativní aplikace.|-   [Použití metod profilace z příkazového řádku](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Služby profilace](../profiling/command-line-profiling-of-services.md)|  
|**Vytváření sestav. XML a. CSV:** Profilování v příkazovém řádku vytvoří datové soubory, které lze zobrazit v rozhraní pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Pomocí nástroje příkazového řádku VSPerfReport můžete také vygenerovat soubory. XML nebo textový soubor s oddělovači (. csv).|-   [Vytváření sestav profileru z příkazového řádku](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Profilování kódu na počítačích bez sady Visual Studio:** K shromažďování dat pro aplikace na počítačích, které nejsou nainstalované, můžete použít Nástroje pro profilaci samostatného profileru [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|-   [Postupy: Instalace samostatného profileru](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## <a name="reference"></a>Odkaz  
 [Odkaz na Nástroje pro profilaci příkazového řádku](../profiling/command-line-profiling-tools-reference.md)  
  
## <a name="see-also"></a>Viz také  
 [Prohlížeč výkonu](../profiling/performance-explorer.md)
