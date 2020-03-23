---
title: Nastavení obecných možností relace výkonu | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773939"
---
# <a name="set-general-performance-session-options"></a>Nastavení obecných možností výkonnostní relace

Metodu kolekce a profilování konvencí pojmenování dat pro relaci výkonu Nástroje profilování sady Visual Studio můžete nastavit na stránce **Obecné** dialogového okna vlastností relace výkonu. Chcete-li otevřít toto dialogové okno z **Průzkumníka výkonu**, klepněte pravým tlačítkem myši na relaci výkonu a potom klepněte na příkaz **Vlastnosti**.

## <a name="choosing-data-collection-methods"></a>Výběr metod sběru dat

Metodu základní kolekce nastavíte výběrem jedné z možností v části **Profilování kolekce**. Možnosti jsou popsány v následující tabulce:

|||
|-|-|
|**Odběr vzorků**. Metoda odběru vzorků shromažďuje informace o profilování v pravidelných intervalech. Tato metoda je užitečná pro hledání problémů s využitím procesoru a je navrhovanou metodou pro spuštění většiny šetření výkonu.|- [Shromažďování statistik výkonu pomocí vzorkování](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Instrumentace**. Instrumentace metoda vloží do kopie kódu profilování modulu, který zaznamenává každý vstup, ukončení a volání funkce funkcí v modulu během profilování spustit. Tato metoda je užitečná pro shromažďování podrobné informace o časování o části kódu a pro pochopení dopadu vstupních a výstupních operací na výkon aplikace.|- [Shromažďování podrobných časovacích dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Souběžnost**. Metoda souběžnosti shromažďuje data pro každou událost, která blokuje spuštění kódu, například když vlákno čeká na uzamčený přístup k prostředku aplikace, který má být uvolněn. Tato metoda je užitečná pro analýzu vícevláknových aplikací.|- [Shromažďování dat souběžnosti vláken a procesů](../profiling/collecting-thread-and-process-concurrency-data.md)|

 Můžete shromažďovat data paměti .NET pomocí metody vzorkování nebo instrumentace. Typ dat vyberte v části **profilování paměti .NET**.

|||
|-|-|
|**Shromažďujte informace o přidělení objektu .NET**. Ve výchozím nastavení data zahrnují počet a velikost přidělených objektů. Zaškrtnutím nebo zrušením zaškrtnutí tohoto políčka povolíte nebo zakážete shromažďování dat paměti .NET. |- [Shromažďování dat přidělení paměti .NET a životnosti](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|
|**Shromažďujte také informace o životnosti objektu .NET**. Zaškrtnutím tohoto políčka zahrnete data o generacích uvolňování paměti, které byly použity k uvolnění paměťových objektů.|- [Shromažďování dat přidělení paměti .NET a životnosti](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) |

 Stránka relace profilování se zobrazí, jakmile začnete profilovat aplikaci. Na této stránce můžete profilování pozastavit, obnovit a zastavit.

 ![Stránka relace profilování](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="set-profiling-data-file-options"></a>Nastavení možností souboru datového souboru profilování

|||
|-|-|
|**zpráva**. Ve výchozím nastavení je soubor dat profilování (.vsp) uveden název profilované aplikace a je umístěn ve složce řešení nebo projektu. K názvu je také připojen řetězec kalendářních dat a do datových souborů, které by jinak měly duplicitní názvy, je přidáno větší číslo. Tato nastavení můžete změnit.|- [Postup: Nastavení možností názvu souboru dat výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
