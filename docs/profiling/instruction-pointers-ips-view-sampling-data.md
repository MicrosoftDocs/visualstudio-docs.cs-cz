---
title: Zobrazení ukazatelů instrukcí ( IP ) – vzorkování dat | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 42398e044bfc06e41249b15ac9baeebcaebd19f6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774253"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Zobrazení ukazatelů instrukcí (IP) – vzorkování dat
Zobrazení IP adresy vzorkování dat uvádí údaje o výkonu pro pokyny sestavení, které byly přímo provádění při vzorky byly shromážděny v profilování spustit.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje instrukce.|
|**Cesta modulu**|Cesta modulu, který obsahuje instrukce.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje instrukce.|
|**Název funkce**|Název funkce, která obsahuje instrukce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Počáteční adresa paměti funkce v načteném binárním souboru.|
|**Začátek zdrojového řádku**|Číslo startovní ho řádku ve zdrojovém souboru, ve kterém byla tato ukázka shromážděna.|
|**Konec řádku zdroje**|Koncové číslo řádku ve zdrojovém souboru, ve kterém byla tato ukázka shromážděna.|
|**Začátek znaku zdroje**|Posun počátečního znaku ve řádku zdrojového souboru, na kterém byla tato ukázka shromážděna.|
|**Konec zdrojového znaku**|Posun koncového znaku ve řádku zdrojového souboru, na kterém byla tato ukázka shromážděna.|
|**Adresa instrukce**|Adresa instrukce v načteném binárním souboru.|
|**Exkluzivní ukázky**|Celkový počet vzorků, které byly shromážděny při provádění instrukce.|
|**Exkluzivní vzorky %**|Procento všech vzorků v profilování spustit, které byly shromážděny při provádění instrukce.|

## <a name="see-also"></a>Viz také
- [Zobrazení ukazatelů instrukcí (IP) – vzorkování](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
