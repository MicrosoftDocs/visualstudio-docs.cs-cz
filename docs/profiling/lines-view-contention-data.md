---
title: Zobrazení řádků – data konfliktů | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778593"
---
# <a name="lines-view---contention-data"></a>Zobrazení řádků – data tvrzení
Zobrazení řádky tvrzení data uvádí údaje o výkonu pro příkazy, které byly spuštěny při vzorky byly shromážděny v profilování spustit. Ve zdrojovém souboru může příkaz zahrnovat více než jeden řádek ve zdrojovém souboru a jeden řádek může obsahovat více než jeden příkaz.

 Prohlášení je označeno následujícími údaji:

- Zdrojový soubor, který obsahuje příkaz funkce.

- Funkce, která obsahuje příkaz.

- Zdrojový řádek, na kterém začíná příkaz.

- Znak ve zdrojovém řádku, na kterém začíná příkaz.

- Zdrojový řádek, na kterém končí příkaz.

- Znak ve zdrojovém řádku, na kterém končí příkaz.

  Sloupec Název řádku poskytuje seřaditelné zřetězení dat identifikátoru.

  Následující tabulka popisuje sloupce sestavy Zobrazení řádků.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní blokovaný čas**|Doba, po kterou byl tento příkaz zablokován od spuštění kódu v příkazu z důvodu konfliktní události. Blokovaný čas ve funkcích, které příkaz volá není zahrnuta.|
|**Výhradní blokovaný čas %**|Procento všech blokovaných čas v procesu, který byl výhradní blokovaný čas příkazu.|
|**Exkluzivní tvrzení**|Počet, kolikrát byl tento příkaz zablokován z provádění kódu v příkazu z důvodu konfliktní události. Konflikty události ve funkcích, které příkaz volal nejsou zahrnuty.|
|**Výhradní tvrzení %**|Procento všech konfliktních událostí v procesu, které byly výhradní mise tohoto prohlášení.|
|**Adresa funkce**|Adresa funkce, která obsahuje tento příkaz.|
|**Název funkce**|Plně kvalifikovaný název funkce, která obsahuje tento příkaz.|
|**Včetně blokovaného času**|Blokovaný čas v tomto příkazu a funkce volané v příkazu.|
|**Včetně blokovaného času %**|Procento všech blokovaných čas v procesu, který byl včetně blokované čas příkazu.|
|**Inkluzivní tvrzení**|Počet, kolikrát tento příkaz a funkce, které byly volány v příkazu byly blokovány provádění.|
|**Inkluzivní tvrzení %**|Procento všech konfliktních událostí v procesu, které byly včetně tvrzení tohoto prohlášení.|
|**Název řádku**|Profiler generovaný identifikátor řádku. Identifikátor používá následující syntaxi:`SourceFile`**;[** `LineNumberStart` **,**,`CharacterStart`**]->; [**`LineNumberEnd`**,**`CharacterEnd`**]**|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje příkaz.|
|**Cesta modulu**|Cesta modulu, který obsahuje příkaz.|
|**ID procesu**|ID procesu (PID) profilovaného procesu.|
|**Název procesu**|Název procesu|
|**Začátek znaku zdroje**|Posun počátečního znaku ve řádku zdrojového souboru, na kterém začíná tento příkaz.|
|**Konec zdrojového znaku**|Posun počátečního znaku ve řádku zdrojového souboru, na kterém tento příkaz končí.|
|**Zdrojový soubor**|Název zdrojového souboru, který obsahuje příkaz funkce.|
|**Začátek zdrojového řádku**|Číslo řádku ve zdrojovém souboru, ve kterém začíná příkaz.|
|**Konec řádku zdroje**|Číslo řádku ve zdrojovém souboru, ve kterém příkaz končí.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení řádků](../profiling/lines-view.md)
- [Zobrazení čar - odběr vzorků](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Zobrazení řádků](../profiling/lines-view-sampling-data.md)
