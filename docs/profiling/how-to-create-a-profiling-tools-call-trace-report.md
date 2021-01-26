---
title: Vytvoření sestavy trasování volání Nástroje pro profilaci | Microsoft Docs
description: Vytvoření sestavy trasování volání nástrojů výkonu pro zobrazení informací o časování pro vaše funkce a pro funkce, které jsou volány funkcemi.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b9c979668cdf24fae7acddd259a82e5c62353084
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800420"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Postupy: Vytvoření sestavy trasování volání nástrojů pro profilaci
*Sestava trasování volání* pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci uvádí informace o časování pro každý vstupní a výstupní bod do funkcí aplikace a každé volání dalších funkcí vaší funkcí. Sestavy trasování volání jsou k dispozici pro data profilování pouze v případě, že byla shromážděna pomocí metody instrumentace.

> [!NOTE]
> Sestavy trasování volání nelze zobrazit v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . K vygenerování hodnoty oddělené čárkami je nutné použít nástroj příkazového řádku **VSPerfReport** .*CSV*) nebo. soubor *XML* . Další informace o tomto nástroji naleznete v tématu [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Vytvoření sestavy trasování volání

1. Otevřete okno **příkazového řádku** .

2. Do příkazového řádku zadejte následující příkaz:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/XML]**

    |Položka|Popis|
    |-|-|
    |*ToolsPath*|Cesta Nástroje pro profilaci nástrojů příkazového řádku Další informace najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Data profilace (.*VSP* nebo. *vsps*) souborů. Jsou přijímány úplné a částečné cesty.|
    |XML|Generuje sestavu ve formátu XML.|

## <a name="see-also"></a>Viz také
- [Postupy: shromažďování dat trasování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Rozhraní API nástrojů pro profilaci](../profiling/profiling-tools-apis.md)
