---
title: Zobrazení ukazatelů instrukcí (IP) – vzorkování paměti .NET | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: aa90262081a693227b4594a4e5b7fe22c8fb1627
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778658"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Zobrazení ukazatelů instrukcí (IP) – vzorkovací data paměti .NET
Zobrazení IP adresy pro profilování paměti .NET data, která byla shromážděna pomocí metody vzorkování, uvádí pokyny sestavení, které přidělily paměť během spuštění profilování. Sloupce zobrazení také uvádějí velikost a počet přidělení.

 Jsou uvedeny pouze výhradní hodnoty.

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje instrukce.|
|**Cesta modulu**|Cesta modulu, který obsahuje instrukce.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje instrukce.|
|**Název funkce**|Název funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Počáteční adresa funkce.|
|**Začátek zdrojového řádku**|Číslo startovní ho řádku ve zdrojovém souboru, ve kterém došlo k přidělení.|
|**Konec řádku zdroje**|Koncové číslo řádku ve zdrojovém souboru, ve kterém došlo k přidělení.|
|**Začátek znaku zdroje**|Posun počátečního znaku ve řádku zdrojového souboru, na kterém došlo k přidělení.|
|**Konec zdrojového znaku**|Posun koncového znaku ve řádku zdrojového souboru, na kterém došlo k přidělení.|
|**Adresa instrukce**|Adresa instrukce.|
|**Výhradní přidělení**|Celkový počet objektů, které byly vytvořeny instrukce.|
|**Výhradní přidělení %**|Procento všech objektů, které byly vytvořeny v profilování spustit, které byly přiděleny instrukce.|
|**Exkluzivní bajty**|Počet bajtů paměti, které byly přiděleny v profilování spustit, které byly přiděleny instrukce.|
|**Výhradní bajty %**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly přiděleny instrukce.|

## <a name="see-also"></a>Viz také
- [Zobrazení ukazatelů na instrukce](../profiling/instruction-pointers-ips-view-sampling-data.md)
