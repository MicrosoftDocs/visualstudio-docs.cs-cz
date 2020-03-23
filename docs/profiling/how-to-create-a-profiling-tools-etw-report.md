---
title: 'Postup: Vytvoření sestavy ETW nástrojů profilování | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ce7b02be682d825205fc5fa50d07c1ca817a24d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776398"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Postup: Vytvoření profilovacích nástrojů ETW sestavy
Sestava trasování událostí pro Windows (ETW) uvádí události ETW, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] které jsou zaznamenány v relaci výkonu nástrojů profilování. Data ETW jsou shromažďována v binárním souboru (.* etl*) souboru. Další informace o této sestavě naleznete [v tématu Trasování událostí pro Windows (ETW) sestavy](../profiling/event-tracing-for-windows-etw-report.md).

> [!NOTE]
> V rozhraní aplikace nelze zobrazit sestavy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ETW.

- Informace o shromažďování dat ETW pomocí rozhraní [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]pro aplikaci naleznete v tématu [: Collect Event Tracing for Windows (ETW) data](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Informace o shromažďování dat ETW z příkazového řádku naleznete [v tématu VSPerfCmd](../profiling/vsperfcmd.md) and [Events](../profiling/events-vsperfcmd.md).

  Vygenerujete sestavu ETW pomocí příkazu **VSReport/summary:etw.** Tá. *etl,* který obsahuje data ETW musí být ve stejném adresáři jako data profilování (.* vsp* nebo . *vsps*) Soubor. Ve výchozím nastavení je sestava generována jako hodnota oddělená čárkami (.* csv*). Další informace naleznete [v tématu VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Generování sestavy ETW

- Do okna **příkazového řádku** zadejte následující příkazový řádek:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Souhrn:ETW [/Xml]**

    |||
    |-|-|
    |*Cesta k nástrojům*|Cesta nástroje nástroje profilování. Další informace naleznete [v tématu Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*Soubor VSP*|Data profilování (.* vsp* nebo . *vsps*) Soubor. Jsou přijímány úplné a částečné cesty.|
    |XML|Generuje sestavu, která je formátována ve formátu XML.|
