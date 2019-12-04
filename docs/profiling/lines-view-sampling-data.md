---
title: Zobrazení řádků – vzorkování dat | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778580"
---
# <a name="lines-view---sampling-data"></a>Zobrazení řádků – vzorkování dat
Zobrazení řádky dat vzorkování obsahuje údaje o výkonu pro příkazy, které byly spuštěny, když byly vzorky shromážděny při spuštění profilace.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Ve zdrojovém souboru může příkaz v rámci zdrojového souboru zabírat více než jeden řádek a jeden řádek může obsahovat více než jeden příkaz. Příkaz je identifikován následujícím způsobem:

- Zdrojový soubor, který obsahuje příkaz Function.

- Funkce, která obsahuje příkaz.

- Zdrojový řádek, kde začíná příkaz.

- Znak ve zdrojovém řádku, ve kterém se příkaz spustí.

- Zdrojový řádek, na kterém končí příkaz.

- Znak ve zdrojovém řádku, na kterém končí příkaz.

  Sloupec název čáry poskytuje zřetězení dat identifikátoru.

  Podle definice příkaz nevolá jiné funkce. Proto jsou uvedeny pouze exkluzivní hodnoty.

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu.|
|**Název modulu**|Název modulu, který obsahuje funkci line.|
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci line.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje řádek funkce.|
|**Název funkce**|Název funkce|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Počáteční adresa funkce|
|**Začátek řádku zdroje**|Číslo počátečního řádku ve zdrojovém souboru, ve kterém byl tento vzorek shromážděn.|
|**Konec řádku zdroje**|Číslo koncového řádku ve zdrojovém souboru, ve kterém byl tento vzorový vzorek shromážděn.|
|**Začátek zdrojového znaku**|Posun počátečního znaku v řádku zdrojového souboru, na kterém byla tato ukázka shromážděna.|
|**Konec zdrojového znaku**|Posun koncového znaku na řádku zdrojového souboru, na kterém byla tato ukázka shromážděna.|
|**Název řádku**|Identifikátor vygenerovaný profilerem řádku s následující syntaxí:`Source File` **; [** `Line Number Start` **,** `Character Start` **]->; [** `Line Number End` **,** `Character End` **]**|
|**Exkluzivní vzorky**|Celkový počet vzorků, které byly shromážděny při spuštění funkce line.|
|**% Exkluzivních vzorků**|Procentuální podíl všech vzorků v běhu profilace, které byly shromážděny při spuštění funkce line.|

## <a name="see-also"></a>Viz také:
- [Zobrazení řádků – vzorkování](../profiling/lines-view-dotnet-memory-sampling-data.md)
