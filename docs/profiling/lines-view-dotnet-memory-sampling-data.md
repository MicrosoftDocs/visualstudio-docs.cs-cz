---
title: Zobrazení řádků – vzorkovací data paměti .NET | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 503b3753f4f4fdc98f39804ec767277d7685d0d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774077"
---
# <a name="lines-view---net-memory-sampling-data"></a>Zobrazení řádků – vzorkovací data paměti .NET
Zobrazení Řádky pro data profilování přidělení paměti .NET, která používá metodu vzorkování, uvádí příkazy, které přidělily paměť během spuštění profilování. Sloupce také obsahují velikost a počet přidělení.

 Ve zdrojovém souboru může příkaz zahrnovat více než jeden řádek ve zdrojovém souboru a jeden řádek může obsahovat více než jeden příkaz.

 Prohlášení je označeno:

- Zdrojový soubor, který obsahuje příkaz funkce.

- Funkce, která obsahuje příkaz.

- Zdrojový řádek, na kterém začíná příkaz.

- Znak ve zdrojovém řádku, na kterém začíná příkaz.

- Zdrojový řádek, na kterém končí příkaz.

- Znak ve zdrojovém řádku, na kterém končí příkaz.

  Sloupec Název řádku poskytuje seřaditelné zřetězení dat identifikátoru.

  Podle definice příkaz nevolá jiné funkce. Proto jsou uvedeny pouze výhradní hodnoty.

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje příkaz.|
|**Cesta modulu**|Cesta modulu, který obsahuje příkaz.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje příkaz.|
|**Název funkce**|Název funkce, která obsahuje příkaz.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Počáteční adresa funkce.|
|**Začátek zdrojového řádku**|Číslo startovní ho řádku ve zdrojovém souboru, ve kterém došlo k přidělení.|
|**Konec řádku zdroje**|Koncové číslo řádku ve zdrojovém souboru, ve kterém došlo k přidělení.|
|**Začátek znaku zdroje**|Posun počátečního znaku ve řádku zdrojového souboru, na kterém došlo k přidělení.|
|**Konec zdrojového znaku**|Posun koncového znaku ve řádku zdrojového souboru, na kterém došlo k přidělení.|
|**Název řádku**|Profiler generovaný identifikátor řádku s následující`Source File`syntaxí:**;[** `Line Number Start` **,**,`Character Start`**]->; [**`Line Number Start,Character Start`**]**|
|**Výhradní přidělení**|Celkový počet objektů, které byly vytvořeny v tomto řádku.|
|**Výhradní přidělení %**|Procento všech objektů, které byly vytvořeny v profilování spustit, které byly přiděleny v tomto řádku.|
|**Exkluzivní bajty**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly přiděleny v tomto řádku.|
|**Výhradní bajty %**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly přiděleny v tomto řádku.|

## <a name="see-also"></a>Viz také
- [Zobrazení řádků](../profiling/lines-view-sampling-data.md)
