---
title: 'Postup: Vytvoření sestavy trasování volání nástrojů profilování | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778983"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Postupy: Vytvoření sestavy trasování volání nástrojů pro profilaci
*Sestava trasování* volání [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pro nástroje profilování uvádí informace o časování pro každou položku a výstupní bod funkcí aplikace a každé volání dalších funkcí vaší funkcí. Sestavy trasování volání jsou k dispozici pro profilování dat pouze v případě, že byly shromážděny pomocí metody instrumentace.

> [!NOTE]
> V aplikaci nelze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]zobrazit sestavy trasování volání. Ke generování **VSPerfReport** hodnoty oddělené čárkami (.* csv*) nebo . *xml.* Další informace o tomto nástroji naleznete [v tématu VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Vytvoření sestavy trasování volání

1. Otevřete okno **příkazového řádku.**

2. Do příkazového řádku zadejte následující příkaz:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**

    |||
    |-|-|
    |*Cesta k nástrojům*|Cesta nástrojů příkazového řádku Nástroje profilování. Další informace naleznete [v tématu Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*Soubor VSP*|Data profilování (.* vsp* nebo . *vsps*) Soubor. Jsou přijímány úplné a částečné cesty.|
    |XML|Generuje sestavu formátovanou xml.|

## <a name="see-also"></a>Viz také
- [Postup: Shromažďování dat sledování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Api nástrojů pro profilování](../profiling/profiling-tools-apis.md)
