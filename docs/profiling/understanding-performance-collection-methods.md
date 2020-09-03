---
title: Porozumění metodám shromažďování informací o výkonu | Microsoft Docs
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ecbabae86b762c9143dba6be5aa0e4683a92b0dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88250767"
---
# <a name="understand-performance-collection-methods"></a>Vysvětlení metod shromažďování výkonu

Nástroje pro profilaci sady Visual Studio poskytují pět metod shromažďování údajů o výkonu. Tento článek popisuje různé metody a navrhuje scénáře, ve kterých může být vhodné shromažďovat data s konkrétní metodou.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Metoda|Popis|
|------------|-----------------|
|[Vzorkování](#sampling)|Shromažďuje statistická data o práci prováděné aplikací.|
|[Instrumentace](#instrumentation)|Shromažďuje podrobné informace o časování jednotlivých volání funkce.|
|[Souběžnost](#concurrency)|Shromažďuje podrobné informace o vícevláknových aplikacích.|
|[Paměť .NET](#net-memory)|Shromažďuje podrobné informace o přidělování a uvolňování paměti .NET.|
|[Interakce vrstev](#tier-interaction)|Shromažďuje informace o synchronních voláních funkcí ADO.NET do databáze SQL Server.<br /><br /> Jakákoli edice sady Visual Studio může shromažďovat data profilu interakce vrstev. Tato data však můžete zobrazit pouze v Visual Studio Enterprise.|

Pomocí některých metod profilace můžete také shromažďovat další data, jako jsou čítače výkonu software a hardware. Další informace najdete v tématu [shromažďování dalších údajů o výkonu](../profiling/collecting-additional-performance-data.md).

## <a name="sampling"></a>Vzorkování

Metoda profilování vzorkování shromažďuje statistická data o práci, kterou aplikace provede během profilace. Metoda vzorkování je odlehčená a má malý vliv na spouštění metod aplikace.

Vzorkování je výchozí metoda nástrojů pro profilaci sady Visual Studio. Je vhodný pro následující úlohy:

- Počáteční průzkum výkonu vaší aplikace
- Zkoumání problémů s výkonem, které zahrnují použití mikroprocesoru (CPU)

Metoda profilování vzorkování přerušuje procesor počítače v nastavených intervalech a shromáždí zásobník volání funkce. Pro funkci, která je spuštěná, se zvyšuje počet exkluzivních vzorků. Celkové počty jsou zvyšovány pro všechny volání funkcí v zásobníku volání. Sestavy vzorkování obsahují součty těchto počtů pro profilované moduly, funkce, řádky zdrojového kódu a instrukce.

Ve výchozím nastavení profiler nastaví interval vzorkování na cykly procesoru. Typ intervalu můžete změnit na jiný čítač výkonu procesoru nebo nastavit počet událostí čítače pro daný interval. Můžete také shromažďovat data profilování interakce vrstev (TIP). Tato data obsahují informace o dotazech, které se provedou v databázi SQL Server, prostřednictvím ADO.NET.

[Shromažďování statistik výkonu pomocí vzorkování](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)

[Ukázka zobrazení dat metody](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>Instrumentace

Metoda profilace instrumentace shromažďuje podrobné časování pro volání funkcí v profilované aplikaci. Profilace instrumentace je užitečná pro tyto úlohy:

- Zkoumání kritických bodů vstupu a výstupu, jako je vstupně-výstupní operace disku
- Uzavření kontroly určitého modulu nebo sady funkcí

Metoda instrumentace vloží kód do binárního souboru. Kód zachycuje informace o časování pro všechny funkce v instrumentované souboru a každá funkce volá tyto funkce. Instrumentace také identifikuje, kdy funkce volá operační systém pro operace, jako je zápis do souboru.

Sestavy instrumentace používají tyto čtyři hodnoty k vyjádření celkového času stráveného ve funkci nebo na řádku zdrojového kódu:

- Uplynulý včetně – celkový čas strávený spouštěním funkce nebo řádku zdrojového kódu.

- Aplikace (včetně) – čas strávený spouštěním funkce nebo řádku zdrojového kódu. Volání do operačního systému jsou vyloučena.

- Uplynulý výhradní čas – čas strávený spouštěním funkce nebo řádku zdrojového kódu. Volání dalších funkcí jsou vyloučena.

- Exkluzivní aplikace – čas strávený spouštěním funkce nebo řádku zdrojového kódu. Volání na operační systém nebo jiné funkce jsou vyloučené.

Pomocí metody instrumentace můžete také shromažďovat čítače výkonu CPU i software.

[Porozumění hodnotám dat instrumentace](../profiling/understanding-instrumentation-data-values.md)

[Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>Souběžnost

Profilace souběžnosti shromažďuje informace o vícevláknových aplikacích. Profilování kolizí prostředků shromažďuje podrobné informace o zásobníku volání, kdykoli konkurenční vlákna čekají na přístup ke sdílenému prostředku. Vizualizace souběžnosti také shromažďuje obecnější informace o tom, jak aplikace s více vlákny spolupracuje s:

- Využít.
- Hardware.
- Operační systém.
- Jiné procesy v hostitelském počítači.

V sestavách prostředku a obsahu se zobrazují celkový počet sporů. Také oznamují celkový čas, po který jsou moduly, funkce, řádky zdrojového kódu a instrukce pro určitý prostředek očekávány. Grafy časové osy zobrazují spory, jak se objevily.

Vizualizátor souběžnosti zobrazuje grafické informace, které vám pomůžou najít:

- Kritická místa výkonu.
- Nevyužití procesoru.
- Spor vlákna.
- Migrace vlákna.
- Zpoždění synchronizace.
- Oblasti překrývajících se vstupně-výstupní operace.

  Pokud je to možné, grafický výstup odkazuje na data ze zásobníku volání a zdrojového kódu. Data vizualizace souběžnosti se dají shromažďovat jenom pro aplikace z příkazového řádku a pro aplikace pro Windows.

[Porozumění hodnotám dat kolizí prostředků](../profiling/understanding-resource-contention-data-values.md)

[Shromažďování dat o souběžnosti vláken a procesů](../profiling/collecting-thread-and-process-concurrency-data.md)

[Zobrazení dat kolizí prostředků](../profiling/resource-contention-data-views.md)

[Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>Paměť .NET

Metoda profilování pro alokaci paměti .NET přerušuje CPU při každém přidělení objektu .NET Framework v profilované aplikaci. Když Profiler také shromažďuje data o životnosti objektů, přeruší procesor po každém .NET Framework uvolňování paměti.

Profiler shromažďuje informace o typu, velikosti a počtu objektů vytvořených v rámci přidělení nebo zničení v uvolňování paměti.

- Při výskytu události přidělení shromáždí profiler další informace o zásobníku volání funkce. Profiler zvyšuje počet exkluzivních přidělení pro aktuálně běžící funkci. Také zvyšuje celkové počty pro všechny volání funkcí v zásobníku volání. Sestavy .NET obsahují součty těchto počtů pro profilované typy, moduly, funkce, řádky zdrojového kódu a instrukce.

- Když dojde k uvolnění paměti, Profiler shromáždí data o zničených objektech a o objektech v každé generaci uvolňování paměti. Na konci profilace se v profileru zaznamenávají data o objektech, které se explicitně nezničily. Sestava doba života objektu zobrazí součty pro každý typ přidělený při spuštění profilace.

Profilaci paměti .NET můžete použít buď v režimu vzorkování, nebo v režimu instrumentace. Režim, který vyberete, nemá vliv na sestavy přidělení a životnosti objektů, které jsou jedinečné pro profilaci paměti .NET.

- Při spuštění profilování paměti .NET v režimu vzorkování používá Profiler jako interval události přidělení paměti. V sestavách se zobrazí také celkový počet přidělených objektů a bajtů jako celková a exkluzivní hodnota.

- Když spustíte profilaci paměti .NET v režimu instrumentace, Profiler shromáždí podrobné informace o časování spolu s hodnotami celkových a exkluzivního přidělení.

[Informace o přidělování paměti a hodnotách životnosti objektů a dat](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[Shromažďování dat o alokaci paměti a době platnosti objektů .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>Interakce vrstev

Profilování interakce vrstev přidává informace do datového souboru profilování o synchronních [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] voláních mezi [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] stránkou nebo jinou aplikací a [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] databází. Data zahrnují počet a dobu volání a maximum a minimální časy. Do profilování dat, která shromažďujete pomocí vzorkování, instrumentace, paměti .NET nebo metod souběžnosti, můžete přidat data vrstev interakce.

![Tok dat profilování interakce vrstev](../profiling/media/tierinteraction_profilingtools.png "Tok dat profilování interakce vrstev")

Informace o datech interakce vrstev, která se shromažďují pomocí nástrojů pro profilaci, najdete v následujících článcích.

[Shromáždit data interakce vrstev](../profiling/collecting-tier-interaction-data.md)

[Zobrazení interakce vrstev](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Viz také

[Postupy: shromažďování údajů o výkonu webu](../profiling/how-to-collect-performance-data-for-a-web-site.md)

[Průvodce profilací výkonu pro začátečníky](../profiling/beginners-guide-to-performance-profiling.md)
