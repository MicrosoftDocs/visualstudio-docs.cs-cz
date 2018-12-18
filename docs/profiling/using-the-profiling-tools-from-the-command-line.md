---
title: Pomocí profilace z příkazového řádku nástroje | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac28817a7c72b7ecfbbc3c76dd3626f0a24d11c9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882324"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Použití nástrojů pro profilaci z příkazového řádku
Můžete použít nástroje příkazového řádku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroje pro profilaci sady do profilu aplikace příkazového řádku a k automatizaci profilace pomocí dávkových souborech a skriptování. Můžete také vygenerovat soubory sestav z příkazového řádku. Zjednodušené samostatného profileru můžete použít ke shromažďování dat na počítačích, které nemají [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nainstalované.  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Běžné úlohy  
  
| Úloha | Související obsah |
| - | - |
| **Nastavit umístění symbolů:** Pokud chcete zobrazit názvy funkcí a parametry, profiler musí mít přístup k symbolu (. *soubor PDB*) soubory profilovaných binárních souborů. Tyto soubory by měly obsahovat soubory symbolů pro Microsoft operační systém a aplikace, které chcete zobrazit v analýze. Abyste měli jistotu, že máte správný, můžete použít veřejné Microsoft symbol server. *pdb* soubory pro binární soubory Microsoft. | -   [Postupy: určení umístění souboru se symboly z příkazového řádku](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Profilace aplikace:** nástrojů příkazového řádku a možnosti, které použijete k profilu cílové aplikace závisí na typu aplikace, metodu profilace a určuje, zda je cíl spravované nebo nativní aplikaci. | -   [Použití metod profilace z příkazového řádku](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Samostatné aplikace profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profil služby](../profiling/command-line-profiling-of-services.md) |
| **Vytvořit sestavy .xml a CSV:** profilaci příkazového řádku vytvoří datové soubory, které lze zobrazit v rozhraní pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Můžete také vygenerovat. *xml* nebo hodnot oddělených čárkami (. *sdílený svazek clusteru*) soubory dat pomocí příkazového řádku nástroje VSPerfReport. | -   [Vytváření sestav profileru z příkazového řádku](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Profilovat kód v počítačích bez sady Visual Studio:** samostatný profiler nástrojů pro profilaci sady můžete použít ke shromažďování dat pro aplikace na počítače, které nemají [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nainstalované. | -   [Postupy: Instalace samostatného profileru](../profiling/how-to-install-the-stand-alone-profiler.md) |
  
## <a name="reference"></a>Odkaz  
 [Odkaz na příkazový řádek nástrojů pro profilaci](../profiling/command-line-profiling-tools-reference.md)  
  
## <a name="see-also"></a>Viz také:  
 [Prohlížeč výkonu](../profiling/performance-explorer.md)