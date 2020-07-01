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
ms.openlocfilehash: 5fe610ea87c492e0bf562fe00145c3abaf76b8ef
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520624"
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

    |Položka|Popis|
    |-|-|
    |*ToolsPath*|Cesta k nástroji Nástroje pro profilaci. Další informace najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Data profilace (.* VSP* nebo. *vsps*) souborů. Jsou přijímány úplné a částečné cesty.|
    |XML|Vygeneruje sestavu, která je naformátovaná v XML.|
