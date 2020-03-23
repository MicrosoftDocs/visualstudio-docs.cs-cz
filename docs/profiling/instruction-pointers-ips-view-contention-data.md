---
title: Zobrazení ukazatelů instrukcí ( IP ) – data konfliktů | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774309"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Zobrazení ukazatelů instrukcí (IP) – data tvrzení
Zobrazení IP adresy dat tvrzení uvádí data pro pokyny sestavení, které byly zablokovány provádění v profilování spustit.

 Následující tabulka vysvětluje hodnoty sloupců v zobrazení Ukazatele instrukcí.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní blokovaný čas**|Blokovaný čas v této funkci.|
|**Výhradní blokovaný čas %**|Procento blokovaného času během provádění instrukce.|
|**Exkluzivní tvrzení**|Počet konfliktů, ke kterým došlo během instrukce byla provedena.|
|**Výhradní tvrzení %**|Procento všech tvrzení v profilování spustit, ke kterým došlo při provádění instrukce.|
|**Adresa funkce**|Počáteční adresa paměti funkce v načteném binárním souboru.|
|**Název funkce**|Název funkce, která obsahuje instrukce.|
|**Adresa instrukce**|Adresa paměti instrukce v načteném binárním souboru.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje instrukce.|
|**Cesta modulu**|Cesta modulu, který obsahuje instrukce.|
|**ID procesu**|ID procesu (PID) profilovaného procesu.|
|**Název procesu**|Název procesu|
|**Začátek znaku zdroje**|Posun znaku ve řádku zdrojového souboru, na kterém začíná tato instrukce.|
|**Konec zdrojového znaku**|Posun znaku ve řádku zdrojového souboru, na kterém tato instrukce končí.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje instrukce.|
|**Začátek zdrojového řádku**|Číslo řádku ve zdrojovém souboru, ve kterém tato instrukce začíná.|
|**Konec řádku zdroje**|Číslo řádku ve zdrojovém souboru, na kterém tato instrukce končí.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení ukazatelů na instrukce](../profiling/instruction-pointers-ips-view.md)
- [Zobrazení ukazatelů instrukcí (IP) – vzorkování](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
- [Zobrazení ukazatelů na instrukce](../profiling/instruction-pointers-ips-view-sampling-data.md)
