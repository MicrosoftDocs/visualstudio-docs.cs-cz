---
title: Zobrazení funkcí – data kolizí | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5874ffc7b4d304d1eaacd78032d657fe6ff31d94
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74780049"
---
# <a name="functions-view---contention-data"></a>Zobrazení funkcí – data kolizí
Zobrazení sestav s daty o kolize zobrazuje funkce v průběhu profilace, které byly během spuštění profilace zablokované.

 V následující tabulce jsou vysvětleny hodnoty, které se zobrazí v zobrazení Functions souboru dat profilování, který byl shromážděn pomocí metody souběžnosti.

|Sloupec|Popis|
|------------|-----------------|
|**Výhradní čas zablokování**|Množství času, během kterého byla tato funkce zablokována při provádění kódu v těle funkce. Čas zablokování ve funkcích, které byly volány funkcí, není zahrnutý.|
|**% Výhradního času zablokování**|Procento veškerého času zablokování v běhu profilace, které bylo výhradním časem zablokování této funkce.|
|**Exkluzivní spory**|Počet, kolikrát byla tato funkce zablokována při provádění kódu v těle funkce. Spory ve funkcích, které byly volány funkcí, nejsou zahrnuty.|
|**% Výhradních sporů**|Procento všech sporů v rámci profilace spuštění bylo exkluzivní pro spory této funkce.|
|**Adresa funkce**|Adresa funkce|
|**Název funkce**|Plně kvalifikovaný název funkce.|
|**Celková doba zablokování**|Čas, kdy byla tato funkce nebo funkce, která byla volána touto funkcí, se zablokovala při provádění.|
|**% Celkového času zablokování**|Procentuální hodnota veškerého času zablokování v běhu profilace, která byla včetně času zablokování této funkce nebo modulu.|
|**Celkové spory**|Počet, kolikrát byla tato funkce nebo funkce, která byla volána touto funkcí, zablokovány pro spuštění.|
|**% Celkových sporů**|Procentuální podíl všech sporů v rámci profilace, kterým byly zahrnuté spory této funkce nebo modulu.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu (PID) procesu, ve kterém byla funkce prováděna.|
|**Název procesu**|Název procesu.|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|

## <a name="see-also"></a>Viz také:
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení funkcí](../profiling/functions-view.md)
- [Zobrazení funkcí – instrumentace](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení funkcí – vzorkování](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Zobrazení funkcí](../profiling/functions-view-instrumentation-data.md)
- [Zobrazení funkcí](../profiling/functions-view-sampling-data.md)
