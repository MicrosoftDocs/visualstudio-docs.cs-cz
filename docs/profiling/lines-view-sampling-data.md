---
title: Zobrazení čar – vzorkovací data | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ff4d851937111400002de531696b9b69aec20ba9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778580"
---
# <a name="lines-view---sampling-data"></a>Zobrazení čar – vzorkovací data
Zobrazení řádky vzorkování dat uvádí údaje o výkonu pro příkazy, které byly spuštěny při vzorkování byly shromážděny v profilování spustit.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Ve zdrojovém souboru může příkaz zahrnovat více než jeden řádek ve zdrojovém souboru a jeden řádek může obsahovat více než jeden příkaz. Prohlášení je označeno:

- Zdrojový soubor, který obsahuje příkaz funkce.

- Funkce, která obsahuje příkaz.

- Zdrojový řádek, na kterém začíná příkaz.

- Znak ve zdrojovém řádku, na kterém začíná příkaz.

- Zdrojový řádek, na kterém končí příkaz.

- Znak ve zdrojovém řádku, na kterém končí příkaz.

  Sloupec Název řádku poskytuje seřaditelné zřetězení dat identifikátoru.

  Podle definice příkaz nevolá jiné funkce. Proto jsou uvedeny pouze výhradní hodnoty.

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje řádek funkce.|
|**Cesta modulu**|Cesta modulu, který obsahuje řádek funkce.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje řádek funkce.|
|**Název funkce**|Název funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Počáteční adresa funkce.|
|**Začátek zdrojového řádku**|Číslo startovní ho řádku ve zdrojovém souboru, ve kterém byla tato ukázka shromážděna.|
|**Konec řádku zdroje**|Koncové číslo řádku ve zdrojovém souboru, ve kterém byla tato ukázka shromážděna.|
|**Začátek znaku zdroje**|Posun počátečního znaku ve řádku zdrojového souboru, na kterém byla tato ukázka shromážděna.|
|**Konec zdrojového znaku**|Posun koncového znaku ve řádku zdrojového souboru, na kterém byla tato ukázka shromážděna.|
|**Název řádku**|Profiler generovaný identifikátor řádku s následující`Source File`syntaxí:**;[** `Line Number Start` **,**,`Character Start`**]->; [**`Line Number End`**,**`Character End`**]**|
|**Exkluzivní ukázky**|Celkový počet vzorků, které byly shromážděny při provádění řádku funkce.|
|**Exkluzivní vzorky %**|Procento všech vzorků v profilování spustit, které byly shromážděny při provádění řádku funkce.|

## <a name="see-also"></a>Viz také
- [Zobrazení čar - odběr vzorků](../profiling/lines-view-dotnet-memory-sampling-data.md)
