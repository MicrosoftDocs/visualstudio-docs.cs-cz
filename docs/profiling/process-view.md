---
title: Zobrazení procesů | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74772173"
---
# <a name="process-view"></a>Zobrazení procesů
Zobrazení procesu zobrazuje data profilování pro procesy a vlákna, které byly provedeny během procesu profilace.

 Procesy jsou uvedené podle názvu. Vlákna jsou uvedena jako podřízené uzly procesu, který je vytvořil. Vlákna jsou pojmenována funkcí, která spustila vlákno nebo popiskem **[ntdll.dll]** , pokud nejsou k dispozici žádné symboly.

 Chcete-li přidat nebo odebrat sloupce, klikněte pravým tlačítkem myši v zobrazení a vyberte možnost **Přidat nebo odebrat sloupce**. Data můžete také seřadit kliknutím na název sloupce. Další informace najdete v tématu [Postup: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md).

 Sloupce zobrazení procesu jsou stejné pro data generovaná pomocí metod vzorkování a instrumentace a pro data, která obsahují data paměti .NET. V následující tabulce jsou popsány hodnoty sloupců.

|Sloupec|Popis|
|------------|-----------------|
|**Jedinečné ID**|Identifikátor generovaný profilerem, který je jedinečný pro proces nebo vlákno.|
|**ID**|Systémem generovaný identifikátor procesu nebo vlákna.|
|**Name**|Název procesu nebo vlákna.|
|**Čas zahájení**|Počet milisekund nebo procesorů od začátku profilace po začátek procesu nebo vlákna.|
|**Čas ukončení**|Počet milisekund nebo procesorů od začátku profilace po konec procesu nebo vlákna.|

## <a name="see-also"></a>Viz také
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
- [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
