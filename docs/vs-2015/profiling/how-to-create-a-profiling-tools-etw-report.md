---
title: 'Postupy: Vytvoření sestavy trasování událostí pro Nástroje pro profilaci | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7dc74f0486ac7196cf406994ee603bc6c0cf4c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548002"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Postupy: Vytvoření sestavy Trasování událostí pro Windows nástrojů pro profilaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sestava trasování událostí pro Windows (ETW) zobrazuje události ETW, které jsou zaznamenány v relaci výkonu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci. Data ETW se shromažďují v binárním souboru (. ETL). Další informace o této sestavě najdete v tématu [Sestava trasování událostí pro Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
> Sestavy ETW nelze zobrazit v rozhraní pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Informace o tom, jak shromažďovat data ETW pomocí rozhraní pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , najdete v tématu [Postupy: shromáždění dat trasování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Informace o tom, jak shromažďovat data ETW z příkazového řádku, najdete v tématu [VSPerfCmd](../profiling/vsperfcmd.md) a [events](../profiling/events-vsperfcmd.md).  
  
  Sestavu ETW vygenerujete pomocí příkazu **VSReport/Summary: ETW** . Soubor. ETL obsahující data ETW musí být ve stejném adresáři jako soubor dat profilování (. vsp nebo. vsps). Ve výchozím nastavení se sestava generuje jako textový soubor s oddělovači (. csv). Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Generování sestavy ETW  
  
- V okně **příkazového řádku** zadejte následující příkazový řádek:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/summary: ETW [/XML]**  
  
    |Element Command|Popis|  
    |-|-|  
    |*ToolsPath*|Cesta k nástroji Nástroje pro profilaci. Další informace najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Soubor dat profilování (. vsp nebo. vsps). Jsou přijímány úplné a částečné cesty.|  
    |XML|Vygeneruje sestavu, která je naformátovaná v XML.|
