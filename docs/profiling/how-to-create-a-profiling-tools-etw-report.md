---
title: 'Postupy: vytvoření sestavy trasování událostí pro Windows nástrojů pro profilaci | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56e064d4c3f3199da2b32ca48858ae27801e4cf5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874786"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Postupy: vytvoření sestavy trasování událostí pro Windows nástrojů pro profilaci
Sestava trasování událostí pro Windows (ETW) obsahuje události trasování událostí pro Windows, které jsou zaznamenány v relaci výkonu z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroje pro profilaci. Data trasování událostí pro Windows se shromažďují v binárním (. *ETL*) soubor. Další informace o této sestavě najdete v tématu [sestavy trasování událostí pro Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  Nelze zobrazit sestavy trasování událostí pro Windows v rozhraní [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- Informace o tom, jak shromažďování dat trasování událostí pro Windows pomocí rozhraní pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], naleznete v tématu [postupy: shromažďování trasování událostí pro Windows (ETW) data](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Informace o tom, jak shromažďovat data trasování událostí pro Windows z příkazového řádku najdete v tématu [VSPerfCmd](../profiling/vsperfcmd.md) a [události](../profiling/events-vsperfcmd.md).  
  
  Generování sestavy trasování událostí pro Windows pomocí **VSReport / summary: etw** příkazu. Na. *etl* trasování událostí pro Windows, který obsahuje data musí být ve stejném adresáři jako dat profilování (. *Vsp* nebo. *vsps*) soubor. Ve výchozím nastavení je sestava generována jako hodnoty oddělené čárkou (. *sdílený svazek clusteru*) soubor. Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Chcete-li generovat sestavu trasování událostí pro Windows  
  
-   V **příkazového řádku** okno, zadejte na příkazovém řádku následující:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **/Summary: ETW [/ XML]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Cesta nástroje pro profilaci. Další informace najdete v tématu [zadejte cestu k nástroji příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Dat profilování (. *Vsp* nebo. *vsps*) soubor. Jsou přijímány úplné a částečné cesty.|  
    |XML|Generuje sestavu, která je ve formátu v jazyce XML.|
