---
title: 'Postupy: Vytvoření sestavy trasování volání Nástroje pro profilaci | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4b184310d837193679a1a5eacf2fbae4ecf29caa
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778983"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Postupy: Vytvoření sestavy trasování volání nástrojů pro profilaci
*Sestava trasování volání* pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroje pro profilaci uvádí informace o časování pro každý vstupní a výstupní bod do funkcí aplikace a každé volání dalších funkcí vaší funkcí. Sestavy trasování volání jsou k dispozici pro data profilování pouze v případě, že byla shromážděna pomocí metody instrumentace.

> [!NOTE]
> V [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nelze zobrazit sestavy trasování volání. K vygenerování hodnoty oddělené čárkami je nutné použít nástroj příkazového řádku **VSPerfReport** . *CSV*) nebo. soubor *XML* . Další informace o tomto nástroji naleznete v tématu [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Vytvoření sestavy trasování volání

1. Otevřete okno **příkazového řádku** .

2. V příkazovém řádku zadejte následující příkaz:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/XML]**

    |||
    |-|-|
    |*ToolsPath*|Cesta Nástroje pro profilaci nástrojů příkazového řádku Další informace najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Data profilace (. *VSP* nebo. *vsps*) souborů. Jsou přijímány úplné a částečné cesty.|
    |XML|Generuje sestavu ve formátu XML.|

## <a name="see-also"></a>Viz také:
- [Postupy: shromažďování dat trasování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Rozhraní API nástrojů pro profilaci](../profiling/profiling-tools-apis.md)
