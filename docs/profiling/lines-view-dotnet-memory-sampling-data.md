---
title: Zobrazení řádků – data vzorkování paměti .NET | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74774077"
---
# <a name="lines-view---net-memory-sampling-data"></a>Zobrazení řádků – data vzorkování paměti .NET
Zobrazení řádků pro data profilování alokace paměti .NET, která používají metodu vzorkování, vypisuje příkazy, které přidělené paměti během profilování běhu. Sloupce také obsahují velikost a počet přidělení.

 Ve zdrojovém souboru může příkaz v rámci zdrojového souboru zabírat více než jeden řádek a jeden řádek může obsahovat více než jeden příkaz.

 Příkaz je identifikován následujícím způsobem:

- Zdrojový soubor, který obsahuje příkaz Function.

- Funkce, která obsahuje příkaz.

- Zdrojový řádek, ve kterém se příkaz spustí.

- Znak ve zdrojovém řádku, ve kterém se příkaz spustí.

- Zdrojový řádek, na kterém končí příkaz.

- Znak ve zdrojovém řádku, na kterém končí příkaz.

  Sloupec název čáry poskytuje zřetězení dat identifikátoru.

  Podle definice příkaz nevolá jiné funkce. Proto jsou uvedeny pouze exkluzivní hodnoty.

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu.|
|**Název modulu**|Název modulu, který obsahuje příkaz.|
|**Cesta k modulu**|Cesta modulu, který obsahuje příkaz.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje příkaz.|
|**Název funkce**|Název funkce, která obsahuje příkaz.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Počáteční adresa funkce|
|**Začátek řádku zdroje**|Číslo počátečního řádku ve zdrojovém souboru, u kterého došlo k přidělení.|
|**Konec řádku zdroje**|Číslo koncového řádku ve zdrojovém souboru, u kterého došlo k přidělení.|
|**Začátek zdrojového znaku**|Posun počátečního znaku v řádku zdrojového souboru, kdy došlo k přidělení.|
|**Konec zdrojového znaku**|Posun koncového znaku v řádku zdrojového souboru, kdy došlo k přidělení.|
|**Název řádku**|Identifikátor vygenerovaný profilerem řádku s následující syntaxí:`Source File` **; [** `Line Number Start` **,** `Character Start` **] – >; [** `Line Number Start,Character Start` **]**|
|**Exkluzivní přidělení**|Celkový počet objektů, které byly vytvořeny na tomto řádku.|
|**% Exkluzivní alokace**|Procentuální podíl všech objektů, které byly vytvořeny při spuštění profilace, které byly přiděleny na tomto řádku.|
|**Exkluzivní počet bajtů**|Procento všech bajtů paměti, které byly přiděleny při spuštění profilace, které byly přiděleny na tomto řádku.|
|**% Exkluzivních bajtů**|Procento všech bajtů paměti, které byly přiděleny při spuštění profilace, které byly přiděleny na tomto řádku.|

## <a name="see-also"></a>Viz také:
- [Zobrazení řádků](../profiling/lines-view-sampling-data.md)
