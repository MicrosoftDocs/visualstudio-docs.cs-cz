---
title: 'Postupy: filtrování sestav z příkazového řádku | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db2c9d845af962fc17da1ebd84e8dd5fe6ffadab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146001"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Postupy: Filtrování sestav z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
