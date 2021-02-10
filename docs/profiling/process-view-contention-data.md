---
title: Zobrazení procesu – data kolizí | Microsoft Docs
description: Přečtěte si, jak zobrazení procesu zobrazuje data kolizí pro procesy a vlákna, které byly provedeny během procesu profilace.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 60f137c470b31ddccfa9b26cb907b13288d07dc1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957306"
---
# <a name="process-view---contention-data"></a>Zobrazení procesu – data kolizí
Zobrazení procesu zobrazuje data kolizí pro procesy a vlákna, které byly provedeny během procesu profilace.

 Když jsou symboly k dispozici, jsou procesy uvedeny podle názvu. Pokud symboly nejsou k dispozici, jsou procesy uvedeny podle adresy paměti v šestnáctkovém formátu. Vlákna jsou uvedena jako podřízené položky procesu, který je vytvořil.

 V následující tabulce jsou vysvětleny hodnoty sloupců v tabulce zobrazení procesu.

|Sloupec|Popis|
|------------|-----------------|
|**Čas zahájení**|Počet milisekund nebo procesorů od začátku profilace po začátek procesu nebo vlákna.|
|**Čas zablokování**|Celková doba, během které bylo zablokováno provádění funkcí procesu nebo vlákna.|
|**% Času zablokování**|Procento doby životnosti procesu nebo vlákna, ve kterém bylo zablokováno provádění funkcí procesu nebo vlákna.|
|**Sporů**|Počet, kolikrát byly zablokovány funkce procesu nebo vlákna.|
|**Sporů**|Procentuální podíl všech sporů v rámci profilace, které byly spory procesu nebo vlákna.|
|**Čas ukončení**|Počet milisekund nebo procesorů od začátku profilace po konec procesu nebo vlákna.|
|**ID**|Systémem generovaný identifikátor procesu nebo vlákna.|
|**Doba života**|Počet milisekund nebo procesorů od začátku procesu nebo vlákna na konec procesu nebo vlákna nebo konec profilace.|
|**Typ**|Typ řádku, buď proces, nebo vlákno.<br /><br /> Pouze v sestavách příkazového řádku **VSReport** . Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md).|
|**Název**|Název procesu nebo vlákna.|
|**Jedinečné ID**|Identifikátor generovaný profilerem, který je jedinečný pro proces nebo vlákno.|

## <a name="see-also"></a>Viz také
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení procesů](../profiling/process-view.md)
