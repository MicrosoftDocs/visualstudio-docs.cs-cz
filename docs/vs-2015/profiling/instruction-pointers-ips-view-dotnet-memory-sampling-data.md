---
title: Zobrazení ukazatelů na instrukce (IP) – data vzorkování paměti .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd06bc09114785c4359d05e3cda70c3ce7646c9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143675"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Zobrazení ukazatelů na instrukce – data vzorkování paměti .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Zobrazení Ukazatele na instrukce (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)
