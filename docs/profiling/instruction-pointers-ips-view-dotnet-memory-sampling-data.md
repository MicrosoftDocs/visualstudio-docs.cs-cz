---
title: Zobrazení (IP) ukazatele na instrukce – Data vzorkování paměti .NET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3b3d0d0334ed8073a125d8b2c435f8e5d58299d4
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844869"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Zobrazení (IP) ukazatele na instrukce – data vzorkování paměti .NET
Zobrazení IP adres pro rozhraní .NET paměti přidělení profilování data, která nebyla shromážděna pomocí metody vzorkování uvádí pokyny sestavení, které přidělené paměti při spuštění profilování. Sloupce zobrazení taky seznam velikost a počet přidělení.  
  
 Jsou uvedeny pouze výhradní hodnoty.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**ID procesu**|ID procesu (PID) z profilace spustit.|  
|**Název procesu**|Název procesu.|  
|**Název modulu**|Název modul, který obsahuje pokyn.|  
|**Cesta modulu**|Cesta modul, který obsahuje pokyn.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje pokyn.|  
|**Název funkce**|Název funkce.|  
|**Číslo řádku – funkce**|Číslo řádku spuštění této funkce ve zdrojovém souboru.|  
|**Adresa funkce**|Počáteční adresa funkce.|  
|**Začátek řádku zdroje**|Počáteční řádek číslo ve zdrojovém souboru, kdy došlo k chybě přidělení.|  
|**End řádku zdroje**|Koncová číslo řádku ve zdrojovém souboru, kdy došlo k chybě přidělení.|  
|**Začátek znaku zdroje**|Posun počáteční znak v řádku souboru zdroje, kdy došlo k přidělení.|  
|**End znaku zdroje**|Posun ukončovací znak v řádku souboru zdroje, kdy došlo k přidělení.|  
|**Adresa instrukce**|Adresa instrukce.|  
|**Výhradní přidělení**|Celkový počet objektů, které byly vytvořeny podle pokynů.|  
|**Výhradní přidělení %**|Procento všechny objekty vytvořené v profilaci spuštění, které byly přiděleny podle pokynů.|  
|**Výhradní bajtů**|Počet bajtů paměti, které byly přiděleny v profilaci spuštění, které byly přiděleny podle pokynů.|  
|**% Výhradní bajtů**|Procento všech bajtů paměti, které byly přiděleny v profilaci spuštění, které byly přiděleny podle pokynů.|  
  
## <a name="see-also"></a>Viz také:  
 [Zobrazení ukazatelů na instrukce](../profiling/instruction-pointers-ips-view-sampling-data.md)