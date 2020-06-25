---
title: Postup vytvoření Nástroje pro profilaci sestavy ETW | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 622015ecbc2730c5b0a8cdf7b2ba92c4f5963886
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329814"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Postupy: Vytvoření sestavy ETW nástrojů pro profilaci
Sestava trasování událostí pro Windows (ETW) zobrazuje události ETW, které jsou zaznamenány v relaci výkonu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci. Data ETW se shromažďují v binárním souboru (.* ETL*). Další informace o této sestavě najdete v tématu [Sestava trasování událostí pro Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).

> [!NOTE]
> Sestavy ETW nelze zobrazit v rozhraní pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Informace o tom, jak shromažďovat data ETW pomocí rozhraní pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , najdete v tématu [Postupy: shromáždění dat trasování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Informace o tom, jak shromažďovat data ETW z příkazového řádku, najdete v tématu [VSPerfCmd](../profiling/vsperfcmd.md) a [events](../profiling/events-vsperfcmd.md).

  Sestavu ETW vygenerujete pomocí příkazu **VSReport/Summary: ETW** . Okně. *ETL* obsahující data ETW musí být ve stejném adresáři jako data profilace (.* VSP* nebo. *vsps*) souborů. Ve výchozím nastavení se sestava generuje jako hodnota oddělená čárkou (.* CSV*) soubor. Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Generování sestavy ETW

- V okně **příkazového řádku** zadejte následující příkazový řádek:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/summary: ETW [/XML]**

    |||
    |-|-|
    |*ToolsPath*|Cesta k nástroji Nástroje pro profilaci. Další informace najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Data profilace (.* VSP* nebo. *vsps*) souborů. Jsou přijímány úplné a částečné cesty.|
    |XML|Vygeneruje sestavu, která je naformátovaná v XML.|
