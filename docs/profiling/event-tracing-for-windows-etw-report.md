---
title: Sestava trasování událostí pro Windows (ETW) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74779295"
---
# <a name="event-tracing-for-windows-etw-report"></a>Sestava trasování událostí pro Windows (ETW)
Sestava trasování událostí pro Windows (ETW) zobrazuje události ETW, které byly zaznamenány v relaci výkonu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci. Data ETW se shromažďují v binárním souboru (.* ETL*).

> [!NOTE]
> V rozhraní nemůžete zobrazit sestavy ETW [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Informace o tom, jak shromažďovat trasování událostí pro Windows pomocí Nástroje pro profilaci z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozhraní, najdete v tématu [Postupy: shromáždění dat trasování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Informace o tom, jak shromažďovat data ETW pomocí nástrojů příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) , najdete v tématu [události](../profiling/events-vsperfcmd.md).

- Sestavu ETW vygenerujete pomocí příkazu **VSReport/Summary: ETW** . Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md).

|Sloupec|Popis|
|------------|-----------------|
|**Timestamp**|Určuje, kdy došlo k události.|
|**ID procesu**|Určuje proces, který vygeneroval událost.|
|**ID vlákna**|Identifikuje vlákno, které událost vygenerovalo.|
|**Popis**|Identifikuje poskytovatele událostí.|
|**Typ**|Identifikuje typ události.|
|**Vlastnosti**|Vlastnosti události Každá událost je dvojice název-hodnota oddělená čárkou, která je uzavřená v závorkách.|
