---
title: Filtrování sestav z příkazového řádku | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b6408975e8a3d7189db26913f3de75ad1c7c595
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851135"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Postupy: Filtrování sestav z příkazového řádku
Pomocí možností pro příkaz **VSPerfReport** můžete filtrovat sestavy na konkrétní časové segmenty souboru dat profilování nebo omezit data na jeden nebo více procesů nebo vláken. Další informace o tomto příkazu najdete v tématu [VSPerfReport](../profiling/vsperfreport.md).

|Možnosti|Description|
|-------------|-----------------|
|**Čas_spuštění:**[*hodnota*]|Zobrazit pouze data shromážděná po hodnotě (v milisekundách)|
|**Čas_ukončení:**[*hodnota*]|Zobrazit pouze data shromážděná před hodnotou (v milisekundách)|
|**FilterFile:**`VSPFFile`|Určuje umístění souboru filtru, který byl vygenerován z okna **Sestava výkonu sady Visual Studio** .|
|**MsFilter:**[*čas_spuštění, Duration*]|Zobrazit pouze data z `StartTime` až do délky `Duration` (v milisekundách)|
|**Proces:**[*PID*]|Zobrazit pouze data ze zadaného procesu.|
|**Vlákno:**[*IDvlákna*]|Zobrazit pouze data ze zadaného vlákna.|
|**Vlákno:**[*IDvlákna, ProcessID*]|Zobrazit pouze data ze zadaného vlákna, která jsou přidružena k zadanému procesu.|
