---
title: Zobrazení funkcí – vzorkovací data | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 70fda712a29ff07ee34a4ac76a06198cb5ead8a5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780023"
---
# <a name="functions-view---sampling-data"></a>Zobrazení funkcí - vzorkovací data
Zobrazení sestavy Funkce pro metodu profilů vzorkování uvádí funkce, které byly vzorkovány během spuštění profilování.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|
|**Název funkce**|Plně kvalifikovaný název funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Adresa funkce.|
|**Včetně vzorků**|Celkový počet vzorků, které byly shromážděny při provádění této funkce; to znamená počet vzorků, které byly shromážděny, když tato funkce byla v zásobníku volání. Číslo zahrnuje vzorky, které byly shromážděny při provádění funkcí, které byly volány touto funkcí.|
|**Včetně vzorků %**|Procento všech vzorků v profilování spustit, které byly včetně vzorky této funkce.|
|**Exkluzivní ukázky**|Celkový počet vzorků, které byly shromážděny při provádění kódu v těle této funkce; to znamená, když tato funkce byla v horní části zásobníku volání. Vzorky, které byly shromážděny ve funkcích, které byly volány touto funkcí nejsou zahrnuty.|
|**Exkluzivní vzorky %**|Procento všech vzorků v profilování spustit, které byly výhradní ukázky této funkce.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení funkcí - instrumentace](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení funkcí - vzorkování](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Zobrazení funkcí](../profiling/functions-view-instrumentation-data.md)
