---
title: Vytvoření sestavy trasování volání Nástroje pro profilaci | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 1d7d315d1931dfa64ce0070790c833651fa4fc11
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851200"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Postupy: Vytvoření sestavy trasování volání nástrojů pro profilaci
*Sestava trasování volání* pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci uvádí informace o časování pro každý vstupní a výstupní bod do funkcí aplikace a každé volání dalších funkcí vaší funkcí. Sestavy trasování volání jsou k dispozici pro data profilování pouze v případě, že byla shromážděna pomocí metody instrumentace.

> [!NOTE]
> Sestavy trasování volání nelze zobrazit v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . K vygenerování hodnoty oddělené čárkami je nutné použít nástroj příkazového řádku **VSPerfReport** .* CSV*) nebo. soubor *XML* . Další informace o tomto nástroji naleznete v tématu [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Vytvoření sestavy trasování volání

1. Otevřete okno **příkazového řádku** .

2. Do příkazového řádku zadejte následující příkaz:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/XML]**

    |Položka|Popis|
    |-|-|
    |*ToolsPath*|Cesta Nástroje pro profilaci nástrojů příkazového řádku Další informace najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Data profilace (.* VSP* nebo. *vsps*) souborů. Jsou přijímány úplné a částečné cesty.|
    |XML|Generuje sestavu ve formátu XML.|

## <a name="see-also"></a>Viz také
- [Postupy: shromažďování dat trasování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Rozhraní API nástrojů pro profilaci](../profiling/profiling-tools-apis.md)
