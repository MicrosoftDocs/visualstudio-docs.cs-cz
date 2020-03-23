---
title: Zobrazení procesů – data konfliktů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 30c938088538bcecc71e3a7e37d5ae403dd476e1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778398"
---
# <a name="process-view---contention-data"></a>Zobrazení procesu – data tvrzení
Zobrazení proces zobrazuje data kolizí pro procesy a vlákna, které byly provedeny během spuštění profilování.

 Pokud jsou k dispozici symboly, procesy jsou uvedeny podle názvu. Pokud symboly nejsou k dispozici, procesy jsou uvedeny podle jejich adresu paměti v šestnáctkovém formátu. Vlákna jsou uvedeny jako podřízené části procesu, který je vytvořil.

 Následující tabulka vysvětluje hodnoty sloupců v tabulce zobrazení Proces.

|Sloupec|Popis|
|------------|-----------------|
|**Počáteční čas**|Počet milisekund nebo cyklů procesoru od začátku profilování do začátku procesu nebo vlákna.|
|**Blokovaný čas**|Celkový čas, během kterého byly funkce procesu nebo vlákna blokovány provádění.|
|**Blokovaný čas %**|Procento životnosti procesu nebo vlákna, ve kterém byly funkce procesu nebo vlákna zablokovány.|
|**Tvrzení**|Počet, kolikrát byly funkce procesu nebo vlákna blokovány v provádění.|
|**Tvrzení %**|Procento všech tvrzení v profilování spustit, které byly tvrzení procesu nebo vlákna.|
|**Čas ukončení**|Počet milisekund nebo cyklů procesoru od začátku profilování do konce procesu nebo vlákna.|
|**Id**|Systémově generovaný identifikátor procesu nebo vlákna.|
|**Životnost**|Počet milisekund nebo cyklů procesoru od začátku procesu nebo vlákna na konec procesu nebo podprocesu nebo konec profilování.|
|**Typ**|Typ řádku, proces nebo vlákno.<br /><br /> Pouze v sestavách příkazového řádku **VSReport.** Další informace naleznete [v tématu VSPerfReport](../profiling/vsperfreport.md).|
|**Název**|Název procesu nebo vlákna.|
|**Jedinečné ID**|Identifikátor generovaný profilerem, který je jedinečný pro proces nebo vlákno.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení procesů](../profiling/process-view.md)
