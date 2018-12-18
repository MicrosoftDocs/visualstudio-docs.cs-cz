---
title: 'Postupy: vytvoření sestavy trasování volání nástrojů pro profilaci | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a363554dfab8463ed91a82ffae9dea4f52d435d4
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815722"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Postupy: vytvoření sestavy trasování volání nástrojů pro profilaci
*Sestavy trasování volání* pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástrojích pro profilaci uvádí informace o časování pro každý vstupní a výstupní bod pro funkce aplikace a každé volání jiných funkcí podle funkce. Jsou k dispozici pro profilace data jenom v případě, že byl shromážděné pomocí metody instrumentace sestavy trasování volání.  
  
> [!NOTE]
>  Nelze zobrazit sestavy trasování volání v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Je nutné použít **vsperfreport –** nástroj příkazového řádku pro generování hodnot oddělených čárkami (. *CSV*) nebo. *xml* souboru. Další informace o tomto nástroji najdete v tématu [vsperfreport –](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Vytvoření sestavy trasování volání  
  
1.  Otevřete **příkazového řádku** okno.  
  
2.  V příkazovém řádku zadejte následující příkaz:  
  
     *ToolsPath* **vsperfreport –** *VSPFile***/CallTrace [XML]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Cesta nástrojích pro profilaci nástroje příkazového řádku. Další informace najdete v tématu [zadejte cestu k nástroje příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Data profilování (. *Vsp* nebo. *vsps*) souboru. Úplné a částečné cesty, jsou přijaty.|  
    |XML|Generuje zprávu formátu XML.|  

  
## <a name="see-also"></a>Viz také:  
 [Postupy: shromažďování dat trasování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Nástroje pro rozhraní API pro profilaci](../profiling/profiling-tools-apis.md)
