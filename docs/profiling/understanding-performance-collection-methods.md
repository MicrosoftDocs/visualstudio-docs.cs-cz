---
title: Principy metody kolekce výkonu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling Tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d278f8ca6019dd8a29d5e4c57e1e191137a32972
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676033"
---
# <a name="understand-performance-collection-methods"></a>Vysvětlení metody kolekce výkonu

Nástroje pro profilaci sady Visual Studio poskytují pět metod, které můžete použít pro shromažďování dat o výkonu. Toto téma popisuje různé metody a předkládá návrhy některých situací, ve kterých mohou být použity konkrétní metody shromažďování dat.

> [!NOTE]
> Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Metoda|Popis|
|------------|-----------------|
|[Vzorkování](#sampling)|Shromažďuje statistická data o práci provedené aplikací.|
|[Instrumentace](#instrumentation)|Shromažďuje podrobné informace o časování jednotlivých volání funkce.|
|[Souběžnost](#concurrency)|Shromažďuje podrobné informace o vícevláknových aplikacích.|
|[Paměť .NET](#net-memory)|Shromažďuje podrobné informace o přidělování a uvolňování paměti .NET.|
|[Interakce vrstev](#tier-interaction)|Shromažďuje informace o synchronních voláních funkcí rozhraní ADO.NET na databázi SQL Server.<br /><br /> Profilování interakce vrstev lze shromažďovat pomocí libovolné edice sady Visual Studio. Nicméně data profilace interakce vrstev lze zobrazit pouze v sadě Visual Studio Enterprise.|

Pomocí některé z metod profilace můžete shromažďovat další data, například čítače výkonu softwaru a hardwaru. Další informace najdete v tématu [shromažďování dalších dat o výkonu](../profiling/collecting-additional-performance-data.md).

## <a name="sampling"></a>Vzorkování

Metoda profilování vzorkování shromažďuje statistická data o práci, kterou aplikace provede během spuštění profilace. Metoda vzorkování je nenáročná a má malý vliv na provádění metod aplikace.

Vzorkování je výchozí metodou nástrojů pro profilaci sady Visual Studio. Je užitečné v následujících situacích:

- Počáteční průzkum výkonu aplikace.
- Prozkoumání problémů s výkonem, které se týkají využití procesoru (CPU).

Metoda profilování vzorkování přerušuje procesor počítače v nastavených intervalech a shromažďuje zásobník volání funkce. Výhradní čítače vzorků jsou zvětšeny pro spuštěnou funkci a zahrnující čítače jsou zvětšeny pro veškerá volání funkcí v zásobníku volání. Sestavy vzorkování obsahují celkový součet těchto počtů pro profilované moduly, funkce, řádky zdrojového kódu a instrukce.

Ve výchozím nastavení profiler nastaví interval vzorkování na cykly procesoru. Typ intervalu můžete změnit na jiný čítač výkonu procesoru a nastavit počet událostí čítače pro interval. Rovněž můžete shromažďovat data profilace interakce vrstev (TIP), která poskytují informace o dotazech, jež byly provedeny na databázi SQL Server prostřednictvím rozhraní ADO.NET.

[Shromažďování statistik výkonu pomocí vzorkování](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Vysvětlení hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)

[Zobrazení dat metod vzorku](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>Instrumentace

Metoda profilace instrumentace shromažďuje podrobná časování pro volání funkcí v profilované aplikaci. Profilace instrumentace je užitečná pro následující případy:

- Ověřování problémových míst vstupů a výstupů, jako jsou například vstupně-výstupní operace disku.
- Uzavření kontroly konkrétního modulu nebo sady funkcí.

Metoda instrumentace vkládá kód do binárního souboru, který zachycuje informace o časování pro každou funkci v instrumentovaném souboru a každé volání funkce, jež je těmito funkcemi provedeno. Instrumentace také identifikuje, kdy funkce volá do běhu operace, jako je například zápis do souboru. Sestavy instrumentace používají pro reprezentaci celkového času stráveného ve funkci nebo na řádku zdrojového kódu čtyři hodnoty:

- Uplynulý celkový čas – Celkový čas, který byl stráven spouštěním funkce nebo řádku kódu.

- Celkový čas aplikace – Čas strávený spouštěním funkce nebo řádku kódu bez času, který byl stráven voláními do operačního systému.

- Uplynulý výhradní čas – Čas strávený spouštěním kódu v těle funkce nebo řádku kódu. Čas strávený spouštěním funkcí, které byly zavolány funkcí nebo řádkem kódu, není zahrnut.

- Výhradní čas aplikace – Čas strávený spouštěním kódu v těle funkce nebo řádku kódu. Čas strávený prováděním volání do operačního systému a čas strávený spouštěním funkcí volaných danou funkcí nebo řádkem kódu není zahrnut.

Pomocí metod instrumentace můžete také shromažďovat čítače výkonu procesoru i softwaru.

[Vysvětlení hodnotám dat instrumentace](../profiling/understanding-instrumentation-data-values.md)

[Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>Souběžnost

Profilace souběžnosti shromažďuje informace o aplikacích s více vlákny. Profilace kolize prostředků shromažďuje podrobné informace o zásobníku volání pokaždé, kdy jsou konkurenční vlákna nucena počkat na přístup ke sdíleným prostředkům. Vizualizace souběžnosti shromažďuje obecnější informace o interakci vícevláknové aplikace se sebou, s hardwarem, s operačním systémem a dalšími procesy na hostitelském počítači:

- Sestavy kolize prostředků zobrazují celkový počet kolizí a celkový čas, který byl vynaložen na čekání na prostředek pro moduly, funkce, řádky zdrojového kódu a instrukce, ve kterých došlo k čekání. Kolize se rovněž zobrazí v grafech časové osy.

- Vizualizátor souběžnosti zobrazí grafické informace, které lze použít k vyhledání problémových míst výkonu, nízkého využití procesoru, kolize vlákna, migrace vlákna, zpoždění synchronizace, míst překrytí vstupu-výstupu a dalších informací. Pokud je to možné, odkazuje grafický výstup na data zásobníku volání a zdrojového kódu. Data vizualizace souběžnosti můžete shromažďovat pouze pro aplikace příkazového řádku a aplikace pro systém Windows.

[Vysvětlení hodnotám dat kolizí prostředku](../profiling/understanding-resource-contention-data-values.md)

[Shromažďování dat o souběžnosti vláken a procesů](../profiling/collecting-thread-and-process-concurrency-data.md)

[Zobrazení dat kolizí prostředku](../profiling/resource-contention-data-views.md)

[Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>Paměť .NET

Metoda profilace alokace paměti .NET přeruší procesor počítače při každém přidělení objektu rozhraní .NET Framework v profilované aplikaci. Při shromažďování dat o době životnosti objektu přerušuje profiler procesor po každém uvolnění paměti rozhraní .NET Framework.

Profiler shromažďuje informace o typu, velikosti a počtu objektů, které byly vytvořeny během přidělování nebo byly zničeny v procesu uvolnění paměti.

- Při výskytu události přidělení shromáždí profiler další informace o zásobníku volání funkce. Výhradní čítače přidělení jsou zvětšeny pro aktuálně prováděnou funkci a zahrnující čítače jsou zvětšeny pro veškerá volání funkcí v zásobníku volání. Sestavy .NET obsahují součty těchto počtů pro profilované typy, moduly, funkce, řádky zdrojového kódu a instrukce.

- Pokud dojde k uvolnění paměti, profiler shromáždí údaje o objektech, které byly zničeny, a informace o objektech v každé generaci uvolňování paměti. Na konci profilování zaznamená profiler údaje o objektech, které nebyly výslovně zničeny. Sestava Doba života objektu zobrazí celkový součet pro každý typ, který byl přidělen během profilování.

Profilování paměti .NET lze použít v režimu vzorkování nebo instrumentace. Vybraný režim neovlivní sestavy Přidělení a Doba života objektu, které jsou jedinečné pro profilaci paměti .NET:

- Při spuštění profilování paměti .NET v režimu vzorkování používá profiler technologie .NET události přidělení paměti jako intervaly a zobrazuje počet objektů, které byly přiděleny, a celkový počet bajtů, jež byly přiděleny jako zahrnuté a výhradní hodnoty v sestavách.

- Při spuštění profilování paměti .NET v režimu instrumentace budou podrobné informace o časování shromážděny společně s výhradními i zahrnutými hodnotami přidělení.

[Vysvětlení paměť přidělení a objekt hodnotám životnosti](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[Shromažďování dat o alokaci paměti a době platnosti objektů .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>Interakce vrstev

Profilování interakce vrstev přidá do datového souboru profilování informace o synchronních voláních [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] mezi stránkou [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nebo jinou aplikací a databází [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. Data obsahují počet a čas volání a maximální a minimální časy. Data interakce vrstev lze přidat mezi data profilace, která jsou shromážděna metodami vzorkování, instrumentace, paměti .NET nebo souběžnosti.

![Profil dat interakce vrstvy](../profiling/media/tierinteraction_profilingtools.png "TierInteraction_ProfilingTools")

Data interakce vrstev, která jsou shromážděna nástroji pro profilaci

[Shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md)

[Zobrazení interakce vrstev](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Viz také:

[Postupy: shromažďování dat o výkonu pro webový server](../profiling/how-to-collect-performance-data-for-a-web-site.md)  
[Průvodce profilací výkonu pro začátečníky](../profiling/beginners-guide-to-performance-profiling.md)