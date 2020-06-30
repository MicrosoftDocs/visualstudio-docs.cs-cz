---
title: 'Postupy: Vytvoření sestavy trasování volání Nástroje pro profilaci | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbf92b38f9408455e10048fbd4a5e84fdf822ea2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547989"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Postupy: Vytvoření sestavy trasování volání nástrojů pro profilaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Sestava trasování volání* pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci uvádí informace o časování pro každý vstupní a výstupní bod do funkcí aplikace a každé volání dalších funkcí vaší funkcí. Sestavy trasování volání jsou k dispozici pro data profilování pouze v případě, že byla shromážděna pomocí metody instrumentace.  
  
> [!NOTE]
> Sestavy trasování volání nelze zobrazit v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . K vygenerování hodnot oddělených čárkami (. csv) nebo souboru XML je nutné použít nástroj příkazového řádku **VSPerfReport** . Další informace o tomto nástroji naleznete v tématu [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Vytvoření sestavy trasování volání  
  
1. Otevřete okno **příkazového řádku**dek.  
  
2. Do příkazového řádku zadejte následující příkaz:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/XML]**  
  
    |Element Command|Popis|
    |-|-|  
    |*ToolsPath*|Cesta Nástroje pro profilaci nástrojů příkazového řádku Další informace najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Soubor dat profilování (. vsp nebo. vsps). Jsou přijímány úplné a částečné cesty.|  
    |XML|Generuje sestavu ve formátu XML.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: shromažďování dat trasování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Rozhraní API nástrojů pro profilaci](../profiling/profiling-tools-apis.md)
