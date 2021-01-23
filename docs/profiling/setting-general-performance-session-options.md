---
title: Nastavení obecných možností relace výkonu | Microsoft Docs
description: Přečtěte si, jak můžete nastavit metodu shromažďování a zásady vytváření názvů dat pro Nástroje pro profilaci výkonnostní relace.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2691d9d8868343291f3be4d9f5b3002e24605b85
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720186"
---
# <a name="set-general-performance-session-options"></a>Nastavení obecných možností výkonnostní relace

Metodu kolekce a zásady vytváření názvů dat profilování pro relaci výkonu sady Visual Studio Nástroje pro profilaci můžete nastavit na stránce **Obecné** v dialogovém okně Vlastnosti pro relaci výkonu. Chcete-li otevřít toto dialogové okno z **prohlížeč výkonu**, klikněte pravým tlačítkem myši na výkonnostní relaci a potom klikněte na příkaz **vlastnosti**.

## <a name="choosing-data-collection-methods"></a>Výběr metod shromažďování dat

Metodu základní kolekce nastavíte tak, že vyberete jednu z možností v části **kolekce profilace**. Možnosti jsou popsány v následující tabulce:

|Možnost|Článek|
|-|-|
|**Vzorkování**. Metoda vzorkování shromažďuje informace profilování v pravidelných intervalech. Tato metoda je užitečná pro hledání problémů s využitím procesoru a je navrhovaná metoda pro spuštění většiny šetření výkonu.|- [Shromažďování statistik výkonu pomocí vzorkování](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Instrumentace**. Metoda instrumentace vloží do kopie kódu profilace modulu, který zaznamenává každé zadání, ukončení a volání funkce v modulu při spuštění profilace. Tato metoda je užitečná pro shromažďování podrobných informací o časování oddílu kódu a pro porozumění dopadu vstupních a výstupních operací na výkon aplikace.|- [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Souběžnost**. Metoda souběžnosti shromažďuje data pro každou událost, která blokuje provádění kódu, například když vlákno čeká na zamčený přístup k prostředku aplikace, který se má uvolnit. Tato metoda je užitečná pro analýzu aplikací s více vlákny.|- [Shromažďování dat o souběžnosti vláken a procesů](../profiling/collecting-thread-and-process-concurrency-data.md)|

 Data paměti .NET můžete shromažďovat pomocí metod vzorkování nebo instrumentace. Vyberte typ dat v části **profilace paměti .NET**.

|Možnost|Článek|
|-|-|
|**Shromažďovat informace o přidělování objektů .NET** Ve výchozím nastavení data obsahují počet a velikost přidělených objektů. Zaškrtnutím nebo zrušením zaškrtnutí tohoto políčka povolíte nebo zakážete shromažďování dat paměti .NET. |- [Shromažďování dat o alokaci paměti a době platnosti .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|
|**Shromažďovat také informace o životnosti objektů .NET**. Toto políčko zaškrtněte, pokud chcete zahrnout data o generacích uvolňování paměti, které byly použity k uvolnění paměťových objektů.|- [Shromažďování dat o alokaci paměti a době platnosti .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) |

 Stránka relace profilování se zobrazí, jakmile začnete profilovat aplikaci. Na této stránce můžete profilování pozastavit, obnovit a zastavit.

 ![Stránka relace profilování](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="set-profiling-data-file-options"></a>Nastavení možností datového souboru profilování

|Možnost|Článek|
|-|-|
|**Sestava**. Ve výchozím nastavení je soubor dat profilování (. vsp) dán názvem profilované aplikace a je umístěn ve složce řešení nebo projektu. K názvu se připojí i řetězec data a do datových souborů, které by jinak měly duplicitní názvy, se přidá přírůstkové číslo. Tato nastavení můžete změnit.|- [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
