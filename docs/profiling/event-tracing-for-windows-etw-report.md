---
title: Sestava sledování událostí pro Windows (ETW) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 19412d184377637c29f34b2fe3ffd033f176b97c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779295"
---
# <a name="event-tracing-for-windows-etw-report"></a>Sestava trasování událostí pro Windows (ETW)
Sestava trasování událostí pro Windows (ETW) uvádí události ETW, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] které byly zaznamenány v relaci výkonu nástrojů profilování. Data ETW jsou shromažďována v binárním souboru (.* etl*) souboru.

> [!NOTE]
> Nelze zobrazit sestavy ETW v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozhraní.

- Informace o tom, jak shromažďovat ETW pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástrojů profilování z rozhraní, naleznete v tématu [How to: Collect Event Tracing for Windows (ETW) data](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Informace o shromažďování dat ETW pomocí nástrojů příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) naleznete v [tématu Události](../profiling/events-vsperfcmd.md).

- Vygenerujete sestavu ETW pomocí příkazu **VSReport/Summary:ETW.** Další informace naleznete [v tématu VSPerfReport](../profiling/vsperfreport.md).

|Sloupec|Popis|
|------------|-----------------|
|**Časové razítko**|Identifikuje, kdy k události došlo.|
|**ID procesu**|Identifikuje proces, který vygeneroval událost.|
|**ID vlákna**|Identifikuje vlákno, které vygenerovalo událost.|
|**Popis**|Identifikuje zprostředkovatele události.|
|**Typ**|Identifikuje typ události.|
|**Vlastnosti**|Vlastnosti události. Každá událost je pár oddělený od čárek a hodnota názvu, který je uzavřen v závorkách.|
