---
title: Zobrazení ukazatelů na instrukce (IP) – data vzorkování paměti .NET
description: Zobrazení IP adres pro data profilování alokace paměti .NET, která byla shromážděna pomocí metody vzorkování, vypíše pokyny pro sestavení, které přidělené paměti.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: d89ede5d7b58bf2605413d8e0621d81983549f34
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721577"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Zobrazení ukazatelů na instrukce (IP) – data vzorkování paměti .NET
Zobrazení IP adres pro data profilování alokace paměti .NET, která byla shromážděna pomocí metody vzorkování, vypíše pokyny pro sestavení, které přidělené paměti při spuštění profilace. Sloupce zobrazení také uvádějí velikost a počet přidělení.

 Jsou uvedeny pouze exkluzivní hodnoty.

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje instrukci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje instrukci.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje instrukci.|
|**Název funkce**|Název funkce|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Počáteční adresa funkce|
|**Začátek řádku zdroje**|Číslo počátečního řádku ve zdrojovém souboru, u kterého došlo k přidělení.|
|**Konec řádku zdroje**|Číslo koncového řádku ve zdrojovém souboru, u kterého došlo k přidělení.|
|**Začátek zdrojového znaku**|Posun počátečního znaku v řádku zdrojového souboru, kdy došlo k přidělení.|
|**Konec zdrojového znaku**|Posun koncového znaku v řádku zdrojového souboru, kdy došlo k přidělení.|
|**Adresa instrukce**|Adresa instrukce|
|**Exkluzivní přidělení**|Celkový počet objektů, které byly vytvořeny instrukcí.|
|**% Exkluzivní alokace**|Procento všech objektů, které byly vytvořeny v průběhu profilace, které byly přiděleny instrukcí.|
|**Exkluzivní počet bajtů**|Počet bajtů paměti, které byly přiděleny při spuštění profilace, které byly přiděleny instrukcí.|
|**% Exkluzivních bajtů**|Procento všech bajtů paměti, které byly přiděleny při spuštění profilace, které byly přiděleny instrukcí.|

## <a name="see-also"></a>Viz také
- [Zobrazení Ukazatele na instrukce (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)
