---
title: 'Postup: Filtrování sestav z příkazového řádku | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1bd6462f9159a2926c6dfa45dcadff860cce9ca1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778931"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Postupy: Filtrování sestav z příkazového řádku
Pomocí možností pro příkaz **VSPerfReport** můžete filtrovat sestavy do určitého časového segmentu datového souboru profilování nebo omezit data na jeden nebo více procesů nebo vláken. Další informace o tomto příkazu naleznete [v tématu VSPerfReport](../profiling/vsperfreport.md).

|Možnosti|Popis|
|-------------|-----------------|
|**Čas spuštění:**[*Hodnota*]|Zobrazit pouze data shromážděná za hodnotou (v milisekundách.)|
|**Koncový čas:**[*Hodnota*]|Zobrazit pouze data shromážděná před hodnotou (v milisekundách.)|
|**Soubor filtru:**`VSPFFile`|Určuje umístění souboru filtru, který byl vygenerován z okna **Sestavy výkonu sady Visual Studio.**|
|**MsFilter:**[*StartTime,Doba trvání*]|Zobrazit pouze `StartTime` data od `Duration` až do délky (v milisekundách.)|
|**Proces:**[*Pid*]|Zobrazit pouze data ze zadaného procesu.|
|**Závit:**[*ThreadID*]|Zobrazit pouze data ze zadaného vlákna.|
|**Vlákno:**[*ThreadID,ProcessID*]|Zobrazit pouze data ze zadaného vlákna, který je přidružen k zadanému procesu.|
