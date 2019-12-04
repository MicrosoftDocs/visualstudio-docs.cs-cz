---
title: Nastavení obecných možností relace výkonu | Microsoft Docs
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
ms.openlocfilehash: 023681b263e6e70048ec7d82d2cee741672989ff
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74773939"
---
# <a name="set-general-performance-session-options"></a>Nastavení obecných možností výkonnostní relace

Metodu kolekce a zásady vytváření názvů dat profilování pro relaci výkonu sady Visual Studio Nástroje pro profilaci můžete nastavit na stránce **Obecné** v dialogovém okně Vlastnosti pro relaci výkonu. Chcete-li otevřít toto dialogové okno z **prohlížeč výkonu**, klikněte pravým tlačítkem myši na výkonnostní relaci a potom klikněte na příkaz **vlastnosti**.

## <a name="choosing-data-collection-methods"></a>Výběr metod shromažďování dat

Metodu základní kolekce nastavíte tak, že vyberete jednu z možností v části **kolekce profilace**. Možnosti jsou popsány v následující tabulce:

|||
|-|-|
|**Vzorkování**. Metoda vzorkování shromažďuje informace profilování v pravidelných intervalech. Tato metoda je užitečná pro hledání problémů s využitím procesoru a je navrhovaná metoda pro spuštění většiny šetření výkonu.|- [shromažďování statistik výkonu pomocí vzorkování](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Instrumentace**. Metoda instrumentace vloží do kopie kódu profilace modulu, který zaznamenává každé zadání, ukončení a volání funkce v modulu při spuštění profilace. Tato metoda je užitečná pro shromažďování podrobných informací o časování oddílu kódu a pro porozumění dopadu vstupních a výstupních operací na výkon aplikace.|- [shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Souběžnost**. Metoda souběžnosti shromažďuje data pro každou událost, která blokuje provádění kódu, například když vlákno čeká na zamčený přístup k prostředku aplikace, který se má uvolnit. Tato metoda je užitečná pro analýzu aplikací s více vlákny.|- [shromažďování dat o souběžnosti vláken a procesů](../profiling/collecting-thread-and-process-concurrency-data.md)|

 Data paměti .NET můžete shromažďovat pomocí metod vzorkování nebo instrumentace. Vyberte typ dat v části **profilace paměti .NET**.

|||
|-|-|
|**Shromažďovat informace o přidělování objektů .NET** Ve výchozím nastavení data obsahují počet a velikost přidělených objektů. Zaškrtnutím nebo zrušením zaškrtnutí tohoto políčka povolíte nebo zakážete shromažďování dat paměti .NET. |- [shromažďování dat o alokaci paměti a době života .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|
|**Shromažďovat také informace o životnosti objektů .NET**. Toto políčko zaškrtněte, pokud chcete zahrnout data o generacích uvolňování paměti, které byly použity k uvolnění paměťových objektů.|- [shromažďování dat o alokaci paměti a době života .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) |

 Stránka relace profilování se zobrazí, jakmile začnete profilovat aplikaci. Na této stránce můžete profilování pozastavit, obnovit a zastavit.

 ![Stránka relace profilování](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="set-profiling-data-file-options"></a>Nastavení možností datového souboru profilování

|||
|-|-|
|**Sestava**. Ve výchozím nastavení je soubor dat profilování (. vsp) dán názvem profilované aplikace a je umístěn ve složce řešení nebo projektu. K názvu se připojí i řetězec data a do datových souborů, které by jinak měly duplicitní názvy, se přidá přírůstkové číslo. Tato nastavení můžete změnit.|- [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
