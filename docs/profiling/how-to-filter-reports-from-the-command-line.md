---
title: Filtrování sestav z příkazového řádku | Microsoft Docs
description: Pomocí VSPerfReport.exe můžete omezit vytváření sestav do konkrétního časového období nebo do vybraných procesů a vláken. V tomto článku jsou uvedené možnosti s popisem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 968b02569c123326710482705146844ef393dfa6
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801202"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Postupy: Filtrování sestav z příkazového řádku
Pomocí možností pro příkaz **VSPerfReport** můžete filtrovat sestavy na konkrétní časové segmenty souboru dat profilování nebo omezit data na jeden nebo více procesů nebo vláken. Další informace o tomto příkazu najdete v tématu [VSPerfReport](../profiling/vsperfreport.md).

|Možnosti|Popis|
|-------------|-----------------|
|**Čas_spuštění:**[*hodnota*]|Zobrazit pouze data shromážděná po hodnotě (v milisekundách)|
|**Čas_ukončení:**[*hodnota*]|Zobrazit pouze data shromážděná před hodnotou (v milisekundách)|
|**FilterFile:**`VSPFFile`|Určuje umístění souboru filtru, který byl vygenerován z okna **Sestava výkonu sady Visual Studio** .|
|**MsFilter:**[*čas_spuštění, Duration*]|Zobrazit pouze data z `StartTime` až do délky `Duration` (v milisekundách)|
|**Proces:**[*PID*]|Zobrazit pouze data ze zadaného procesu.|
|**Vlákno:**[*IDvlákna*]|Zobrazit pouze data ze zadaného vlákna.|
|**Vlákno:**[*IDvlákna, ProcessID*]|Zobrazit pouze data ze zadaného vlákna, která jsou přidružena k zadanému procesu.|
