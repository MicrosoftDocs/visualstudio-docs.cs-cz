---
title: Zobrazení ukazatelů na instrukce (IP) – data kolizí | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f37fb451238ec7ce6f48d8a4d3b91efa9ce04db7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74774309"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Zobrazení ukazatelů na instrukce (IP) – data kolizí
Zobrazení IP adres pro data kolizí obsahuje data pro pokyny k sestavení, které se zablokovaly při spuštění profilace.

 V následující tabulce jsou vysvětleny hodnoty sloupců v zobrazení ukazatelů instrukcí.

|Sloupec|Popis|
|------------|-----------------|
|**Výhradní čas zablokování**|Čas zablokování této funkce.|
|**% Výhradního času zablokování**|Procento času zablokování při spuštění instrukce.|
|**Exkluzivní spory**|Počet sporů, ke kterým došlo během provádění instrukce.|
|**% Výhradních sporů**|Procento všech sporů v průběhu profilace, ke kterým došlo během provádění instrukcí.|
|**Adresa funkce**|Počáteční adresa paměti funkce v načteném binárním souboru.|
|**Název funkce**|Název funkce, která obsahuje instrukci.|
|**Adresa instrukce**|Adresa paměti instrukce v načteném binárním souboru.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje instrukci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje instrukci.|
|**ID procesu**|ID procesu (PID) profilované procesu.|
|**Název procesu**|Název procesu.|
|**Začátek zdrojového znaku**|Posun znaku v řádku zdrojového souboru, na kterém začíná tato instrukce.|
|**Konec zdrojového znaku**|Posun znaku v řádku zdrojového souboru, na kterém končí tato instrukce|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje instrukci.|
|**Začátek řádku zdroje**|Číslo řádku ve zdrojovém souboru, na kterém začíná tato instrukce.|
|**Konec řádku zdroje**|Číslo řádku ve zdrojovém souboru, na kterém končí tato instrukce.|

## <a name="see-also"></a>Viz také:
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení ukazatelů na instrukce](../profiling/instruction-pointers-ips-view.md)
- [Zobrazení ukazatelů na instrukce (IP) – vzorkování](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
- [Zobrazení ukazatelů na instrukce](../profiling/instruction-pointers-ips-view-sampling-data.md)
