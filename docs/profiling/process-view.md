---
title: Zobrazení procesu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: da3097c276557238e6f5b521f6f7d3231434cd10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772173"
---
# <a name="process-view"></a>Zobrazení procesů
Zobrazení proces zobrazuje data profilování pro procesy a vlákna, které byly provedeny během spuštění profilování.

 Procesy jsou uvedeny podle názvu. Vlákna jsou uvedeny jako podřízené uzly procesu, který je vytvořil. Vlákna jsou pojmenována podle funkce, která spustila vlákno, nebo popiskem **[ntdll.dll],** pokud nejsou k dispozici žádné symboly.

 Chcete-li přidat nebo odebrat sloupce, klepněte v zobrazení pravým tlačítkem myši a vyberte příkaz **Přidat nebo odebrat sloupce**. Kromě toho můžete data seřadit klepnutím na název sloupce. Další informace naleznete v [tématu Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md).

 Sloupce zobrazení procesu jsou stejné pro data, která jsou generována pomocí metody vzorkování a instrumentace a pro data, která obsahují data paměti .NET. Následující tabulka popisuje hodnoty sloupců.

|Sloupec|Popis|
|------------|-----------------|
|**Jedinečné ID**|Identifikátor generovaný profilerem, který je jedinečný pro proces nebo vlákno.|
|**Id**|Systémově generovaný identifikátor procesu nebo vlákna.|
|**Název**|Název procesu nebo vlákna.|
|**Počáteční čas**|Počet milisekund nebo cyklů procesoru od začátku profilování do začátku procesu nebo vlákna.|
|**Čas ukončení**|Počet milisekund nebo cyklů procesoru od začátku profilování do konce procesu nebo vlákna.|

## <a name="see-also"></a>Viz také
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
- [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
