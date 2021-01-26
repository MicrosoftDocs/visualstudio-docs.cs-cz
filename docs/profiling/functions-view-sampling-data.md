---
title: Zobrazení funkcí – vzorkování dat | Microsoft Docs
description: Přečtěte si o zobrazení sestav funkcí pro metodu profil vzorkování, která obsahuje seznam funkcí, které byly při spuštění profilování ukázkové.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8f30849ff7503d9301ee94408df0cd7b14f65fea
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801253"
---
# <a name="functions-view---sampling-data"></a>Zobrazení funkcí – vzorkování dat
Zobrazení sestavy funkce pro metodu profil vzorkování obsahuje funkce, které byly během spuštění profilování vzorků popsány.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|
|**Název funkce**|Plně kvalifikovaný název funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Adresa funkce|
|**Vzorky včetně**|Celkový počet vzorků, které byly shromážděny při provádění této funkce; To znamená počet vzorků, které byly shromážděny, pokud byla tato funkce v zásobníku volání. Číslo zahrnuje vzorky, které byly shromážděny v případě, že byly spuštěny funkce, které byly volány touto funkcí.|
|**% Včetně vzorků**|Procentuální podíl všech vzorků v průběhu profilace, které byly zahrnuté do vzorků této funkce.|
|**Exkluzivní vzorky**|Celkový počet vzorků, které byly shromážděny při provádění kódu v těle této funkce; To znamená, že pokud tato funkce byla v horní části zásobníku volání. Vzorky shromážděné ve funkcích, které byly volány touto funkcí, nejsou zahrnuty.|
|**% Exkluzivních vzorků**|Procentuální podíl všech vzorků v rámci profilace spuštění, které byly exkluzivními ukázkami této funkce.|

## <a name="see-also"></a>Viz také
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení funkcí – instrumentace](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení funkcí – vzorkování](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Zobrazení funkcí](../profiling/functions-view-instrumentation-data.md)
