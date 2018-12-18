---
title: Pomocí profilace z příkazového řádku nástroje | Dokumentace Microsoftu
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
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cb3fafa78d49904c346212e8fd4062c966a63f5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775144"
---
# <a name="using-the-profiling-tools-from-the-command-line"></a>Použití nástrojů pro profilaci z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít nástroje příkazového řádku [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástroje pro profilaci sady do profilu aplikace příkazového řádku a k automatizaci profilace pomocí dávkových souborech a skriptování. Můžete také vygenerovat soubory sestav z příkazového řádku. Zjednodušené samostatného profileru můžete použít ke shromažďování dat na počítačích, které nemají [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nainstalované.  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Nastavit umístění symbolů:** Pokud chcete zobrazit názvy funkcí a parametry, profiler musí mít přístup k soubory symbolů (PDB) profilovaných binárních souborů. Tyto soubory by měly obsahovat soubory symbolů pro Microsoft operační systém a aplikace, které chcete zobrazit v analýze. Abyste měli jistotu, že máte soubory s příponou .pdb správné pro binární soubory Microsoft můžete použít veřejné Microsoft symbol server.|-   [Postupy: určení umístění souboru se symboly z příkazového řádku](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Profilace aplikace:** nástrojů příkazového řádku a možnosti, které použijete k profilu cílové aplikace závisí na typu aplikace, metodu profilace a určuje, zda je cíl spravované nebo nativní aplikaci.|-   [Použití metod profilace z příkazového řádku](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profilace služeb](../profiling/command-line-profiling-of-services.md)|  
|**Vytvořit sestavy .xml a CSV:** profilaci příkazového řádku vytvoří datové soubory, které lze zobrazit v rozhraní pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. XML nebo souborů hodnot oddělených čárkami (CSV) dat můžete vygenerovat také pomocí příkazového řádku nástroje VSPerfReport.|-   [Vytváření sestav Profiler z příkazového řádku](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Profilovat kód v počítačích bez sady Visual Studio:** samostatný profiler nástrojů pro profilaci sady můžete použít ke shromažďování dat pro aplikace na počítače, které nemají [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nainstalované.|-   [Postupy: Instalace samostatného Profiler](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## <a name="reference"></a>Odkaz  
 [Referenční dokumentace nástrojů příkazového řádku pro profilaci](../profiling/command-line-profiling-tools-reference.md)  
  
## <a name="see-also"></a>Viz také  
 [Prohlížeč výkonu](../profiling/performance-explorer.md)



