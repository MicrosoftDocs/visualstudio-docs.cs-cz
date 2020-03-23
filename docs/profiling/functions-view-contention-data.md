---
title: Zobrazení funkcí – data konfliktů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5874ffc7b4d304d1eaacd78032d657fe6ff31d94
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780049"
---
# <a name="functions-view---contention-data"></a>Zobrazení funkcí – data tvrzení
Zobrazení sestavy funkce dat tvrzení uvádí funkce v profilování spustit, které byly zablokovány spuštění během profilování spustit.

 Následující tabulka vysvětluje hodnoty, které jsou zobrazeny v zobrazení Funkce profilování datového souboru, který byl shromážděn pomocí metody souběžnosti.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní blokovaný čas**|Doba, po kterou byla tato funkce blokována od spuštění kódu v těle funkce. Blokovaný čas ve funkcích, které byly volány funkcí, není zahrnut.|
|**Výhradní blokovaný čas %**|Procento všech blokovaných čas v profilování spustit, který byl výhradní blokovaný čas této funkce.|
|**Exkluzivní tvrzení**|Počet, kolikrát byla tato funkce blokována ve spuštění kódu v těle funkce. Konflikty ve funkcích, které byly volány funkcí, nejsou zahrnuty.|
|**Výhradní tvrzení %**|Procento všech tvrzení v profilování spustit byly výhradní tvrzení této funkce.|
|**Adresa funkce**|Adresa funkce.|
|**Název funkce**|Plně kvalifikovaný název funkce.|
|**Včetně blokovaného času**|Čas, kdy tato funkce nebo funkce, která byla volána touto funkcí, byla zablokována.|
|**Včetně blokovaného času %**|Procento všech blokovaných čas v profilování spustit, který byl včetně blokované čas této funkce nebo modulu.|
|**Inkluzivní tvrzení**|Počet, kolikrát byla tato funkce nebo funkce, která byla volána touto funkcí, blokována.|
|**Inkluzivní tvrzení %**|Procento všech konfliktů v profilování spustit, které byly včetně tvrzení této funkce nebo modulu.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu, ve kterém byla funkce spuštěna, id procesu.|
|**Název procesu**|Název procesu|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení funkcí](../profiling/functions-view.md)
- [Zobrazení funkcí - instrumentace](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení funkcí - vzorkování](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Zobrazení funkcí](../profiling/functions-view-instrumentation-data.md)
- [Zobrazení funkcí](../profiling/functions-view-sampling-data.md)
