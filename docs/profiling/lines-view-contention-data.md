---
title: Zobrazení řádků – data kolizí | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1dfcdf67c897c0c1565e536a69cc940b9df83390
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778593"
---
# <a name="lines-view---contention-data"></a>Zobrazení řádků – data kolizí
Zobrazení řádky data kolizí obsahuje údaje o výkonu pro příkazy, které byly spuštěny, když byly vzorky shromážděny při spuštění profilace. Ve zdrojovém souboru může příkaz v rámci zdrojového souboru zabírat více než jeden řádek a jeden řádek může obsahovat více než jeden příkaz.

 Příkaz je identifikován následujícími daty:

- Zdrojový soubor, který obsahuje příkaz Function.

- Funkce, která obsahuje příkaz.

- Zdrojový řádek, ve kterém se příkaz spustí.

- Znak ve zdrojovém řádku, ve kterém se příkaz spustí.

- Zdrojový řádek, na kterém končí příkaz.

- Znak ve zdrojovém řádku, na kterém končí příkaz.

  Sloupec název čáry poskytuje zřetězení dat identifikátoru.

  Následující tabulka popisuje sloupce sestavy zobrazení řádků.

|Sloupec|Popis|
|------------|-----------------|
|**Výhradní čas zablokování**|Doba, během které byl tento příkaz zablokován při provádění kódu v příkazu, protože došlo k události sporu. Čas zablokování ve funkcích, které nejsou zahrnuty do příkazu.|
|**% Výhradního času zablokování**|Procento veškerého času zablokování v procesu, který byl výhradním časem zablokování příkazu.|
|**Exkluzivní spory**|Počet, kolikrát byl tento příkaz zablokován při provádění kódu v příkazu, protože došlo k události sporu. Události kolizí ve funkcích, které příkaz nazvaný není zahrnutý.|
|**% Výhradních sporů**|Procento všech událostí sporů v procesu, u kterých došlo k exkluzivnímu sporu tohoto prohlášení.|
|**Adresa funkce**|Adresa funkce, která obsahuje tento příkaz.|
|**Název funkce**|Plně kvalifikovaný název funkce, která obsahuje tento příkaz.|
|**Celková doba zablokování**|Čas zablokování v tomto příkazu a funkcích, které jsou volány v příkazu.|
|**% Celkového času zablokování**|Procento veškerého času zablokování v procesu, který byl zahrnut do času zablokování příkazu.|
|**Celkové spory**|Počet zablokovaných provedení tohoto příkazu a funkcí, které byly volány v příkazu.|
|**% Celkových sporů**|Procento všech událostí sporů v procesu, u kterých byly zahrnuté spory tohoto prohlášení.|
|**Název řádku**|Identifikátor vygenerovaného profilerem. Identifikátor používá následující syntaxi: `SourceFile` **; [** `LineNumberStart` **,**`CharacterStart` **]->; [**`LineNumberEnd`**,**`CharacterEnd`**]**|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje příkaz.|
|**Cesta k modulu**|Cesta modulu, který obsahuje příkaz.|
|**ID procesu**|ID procesu (PID) profilované procesu.|
|**Název procesu**|Název procesu|
|**Začátek zdrojového znaku**|Posun počátečního znaku na řádku zdrojového souboru, na kterém je tento příkaz spuštěn.|
|**Konec zdrojového znaku**|Posun počátečního znaku na řádku zdrojového souboru, na kterém končí tento příkaz.|
|**Zdrojový soubor**|Název zdrojového souboru, který obsahuje příkaz Function.|
|**Začátek řádku zdroje**|Číslo řádku ve zdrojovém souboru, ve kterém se příkaz spustí.|
|**Konec řádku zdroje**|Číslo řádku ve zdrojovém souboru, na kterém končí příkaz.|

## <a name="see-also"></a>Viz také
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení řádků](../profiling/lines-view.md)
- [Zobrazení řádků – vzorkování](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Zobrazení řádků](../profiling/lines-view-sampling-data.md)
