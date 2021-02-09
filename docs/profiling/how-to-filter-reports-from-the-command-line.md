---
title: Filtrování sestav z příkazového řádku | Microsoft Docs
description: Pomocí VSPerfReport.exe můžete omezit vytváření sestav do konkrétního časového období nebo do vybraných procesů a vláken. V tomto článku jsou uvedené možnosti s popisem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dda6b89dcdfacc286417924c666b3ebd805f1cc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897720"
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
