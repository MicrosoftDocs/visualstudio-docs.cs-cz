---
title: Porozumění metodám shromažďování informací o výkonu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling Tools, profiling methods
ms.assetid: ea4881fd-bd04-4875-9b7b-28490d6706f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e398d7e5e297daa68663902efb8a9fa0775c86fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787264"
---
# <a name="understanding-performance-collection-methods"></a>Porozumění metodám shromažďování údajů o výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroje pro profilaci sady Visual Studio poskytují pět metod, které můžete použít pro shromažďování dat o výkonu. Toto téma popisuje různé metody a předkládá návrhy některých situací, ve kterých mohou být použity konkrétní metody shromažďování dat.  
  
> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro Windows Store vyžadují také nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Vzorkování](#sampling)|Shromažďuje statistická data o práci provedené aplikací.|  
|[Instrumentace](#instrumentation)|Shromažďuje podrobné informace o časování jednotlivých volání funkce.|  
|[Souběžnost](#concurrency)|Shromažďuje podrobné informace o vícevláknových aplikacích.|  
|[Paměť .NET](#net_memory)|Shromažďuje podrobné informace o přidělování a uvolňování paměti .NET.|  
|[Interakce vrstev](#tier_interaction)|Shromažďuje informace o synchronních voláních funkcí rozhraní ADO.NET na databázi SQL Server.<br /><br /> Profilování interakce vrstev lze shromažďovat pomocí sady [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] nebo [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Nicméně data profilace interakce vrstev můžete zobrazit pouze v sadě [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] nebo [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].|  
  
 Pomocí některé z metod profilace můžete shromažďovat další data, například čítače výkonu softwaru a hardwaru. Další informace najdete v tématu [shromažďování dalších dat o výkonu](../profiling/collecting-additional-performance-data.md).  
  
## <a name="sampling"></a><a name="sampling"></a> Kontrol  
 Metoda profilování vzorkování shromažďuje statistická data o práci, kterou aplikace provede během spuštění profilace. Metoda vzorkování je nenáročná a má malý vliv na provádění metod aplikace.  
  
 Vzorkování je výchozí metodou nástrojů pro profilaci sady Visual Studio. Je užitečné v následujících situacích:  
  
- Počáteční průzkum výkonu aplikace.  
  
- Prozkoumání problémů s výkonem, které se týkají využití procesoru (CPU).  
  
  Metoda profilování vzorkování přerušuje procesor počítače v nastavených intervalech a shromažďuje zásobník volání funkce. Výhradní čítače vzorků jsou zvětšeny pro spuštěnou funkci a zahrnující čítače jsou zvětšeny pro veškerá volání funkcí v zásobníku volání. Sestavy vzorkování obsahují celkový součet těchto počtů pro profilované moduly, funkce, řádky zdrojového kódu a instrukce.  
  
  Ve výchozím nastavení profiler nastaví interval vzorkování na cykly procesoru. Typ intervalu můžete změnit na jiný čítač výkonu procesoru a nastavit počet událostí čítače pro interval. Rovněž můžete shromažďovat data profilace interakce vrstev (TIP), která poskytují informace o dotazech, jež byly provedeny na databázi SQL Server prostřednictvím rozhraní ADO.NET.  
  
  [Shromažďování statistik výkonu pomocí vzorkování](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
  [Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)  
  
  [Zobrazení dat metod vzorkování](../profiling/profiler-sampling-method-data-views.md)  
  
## <a name="instrumentation"></a><a name="instrumentation"></a> Instrumentace  
 Metoda profilace instrumentace shromažďuje podrobná časování pro volání funkcí v profilované aplikaci. Profilace instrumentace je užitečná pro následující případy:  
  
- Ověřování problémových míst vstupů a výstupů, jako jsou například vstupně-výstupní operace disku.  
  
- Uzavření kontroly konkrétního modulu nebo sady funkcí.  
  
  Metoda instrumentace vkládá kód do binárního souboru, který zachycuje informace o časování pro každou funkci v instrumentovaném souboru a každé volání funkce, jež je těmito funkcemi provedeno. Instrumentace také identifikuje, kdy funkce volá do běhu operace, jako je například zápis do souboru. Sestavy instrumentace používají pro reprezentaci celkového času stráveného ve funkci nebo na řádku zdrojového kódu čtyři hodnoty:  
  
- Uplynulý celkový čas – Celkový čas, který byl stráven spouštěním funkce nebo řádku kódu.  
  
- Celkový čas aplikace – Čas strávený spouštěním funkce nebo řádku kódu bez času, který byl stráven voláními do operačního systému.  
  
- Uplynulý výhradní čas – Čas strávený spouštěním kódu v těle funkce nebo řádku kódu. Čas strávený spouštěním funkcí, které byly zavolány funkcí nebo řádkem kódu, není zahrnut.  
  
- Výhradní čas aplikace – Čas strávený spouštěním kódu v těle funkce nebo řádku kódu. Čas strávený prováděním volání do operačního systému a čas strávený spouštěním funkcí volaných danou funkcí nebo řádkem kódu není zahrnut.  
  
  Pomocí metod instrumentace můžete také shromažďovat čítače výkonu procesoru i softwaru.  
  
  [Porozumění hodnotám dat instrumentace](../profiling/understanding-instrumentation-data-values.md)  
  
  [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)  
  
  [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)  
  
## <a name="concurrency"></a><a name="concurrency"></a> Concurrency  
 Profilace souběžnosti shromažďuje informace o aplikacích s více vlákny. Profilace kolize prostředků shromažďuje podrobné informace o zásobníku volání pokaždé, kdy jsou konkurenční vlákna nucena počkat na přístup ke sdíleným prostředkům. Vizualizace souběžnosti shromažďuje obecnější informace o interakci vícevláknové aplikace se sebou, s hardwarem, s operačním systémem a dalšími procesy na hostitelském počítači:  
  
- Sestavy kolize prostředků zobrazují celkový počet kolizí a celkový čas, který byl vynaložen na čekání na prostředek pro moduly, funkce, řádky zdrojového kódu a instrukce, ve kterých došlo k čekání. Kolize se rovněž zobrazí v grafech časové osy.  
  
- Vizualizátor souběžnosti zobrazí grafické informace, které lze použít k vyhledání problémových míst výkonu, nízkého využití procesoru, kolize vlákna, migrace vlákna, zpoždění synchronizace, míst překrytí vstupu-výstupu a dalších informací. Pokud je to možné, odkazuje grafický výstup na data zásobníku volání a zdrojového kódu. Data vizualizace souběžnosti můžete shromažďovat pouze pro aplikace příkazového řádku a aplikace pro systém Windows.  
  
  [Porozumění hodnotám dat kolizí prostředků](../profiling/understanding-resource-contention-data-values.md)  
  
  [Shromažďování dat o souběžnosti vláken a procesů](../profiling/collecting-thread-and-process-concurrency-data.md)  
  
  [Zobrazení dat kolizí prostředku](../profiling/resource-contention-data-views.md)  
  
  [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)  
  
## <a name="net-memory"></a><a name="net_memory"></a> Paměť .NET  
 Metoda profilace alokace paměti .NET přeruší procesor počítače při každém přidělení objektu rozhraní .NET Framework v profilované aplikaci. Při shromažďování dat o době životnosti objektu přerušuje profiler procesor po každém uvolnění paměti rozhraní .NET Framework.  
  
 Profiler shromažďuje informace o typu, velikosti a počtu objektů, které byly vytvořeny během přidělování nebo byly zničeny v procesu uvolnění paměti.  
  
- Při výskytu události přidělení shromáždí profiler další informace o zásobníku volání funkce. Výhradní čítače přidělení jsou zvětšeny pro aktuálně prováděnou funkci a zahrnující čítače jsou zvětšeny pro veškerá volání funkcí v zásobníku volání. Sestavy .NET obsahují součty těchto počtů pro profilované typy, moduly, funkce, řádky zdrojového kódu a instrukce.  
  
- Pokud dojde k uvolnění paměti, profiler shromáždí údaje o objektech, které byly zničeny, a informace o objektech v každé generaci uvolňování paměti. Na konci profilování zaznamená profiler údaje o objektech, které nebyly výslovně zničeny. Sestava Doba života objektu zobrazí celkový součet pro každý typ, který byl přidělen během profilování.  
  
  Profilování paměti .NET lze použít v režimu vzorkování nebo instrumentace. Vybraný režim neovlivní sestavy Přidělení a Doba života objektu, které jsou jedinečné pro profilaci paměti .NET:  
  
- Při spuštění profilování paměti .NET v režimu vzorkování používá profiler technologie .NET události přidělení paměti jako intervaly a zobrazuje počet objektů, které byly přiděleny, a celkový počet bajtů, jež byly přiděleny jako zahrnuté a výhradní hodnoty v sestavách.  
  
- Při spuštění profilování paměti .NET v režimu instrumentace budou podrobné informace o časování shromážděny společně s výhradními i zahrnutými hodnotami přidělení.  
  
  [Principy přidělování paměti a hodnot dat životnosti objektů](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)  
  
  [Shromažďování dat o přidělení paměti a době platnosti objektů .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
  [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)  
  
## <a name="tier-interaction"></a><a name="tier_interaction"></a> Interakce vrstev  
 Profilování interakce vrstev přidá do datového souboru profilování informace o synchronních voláních [!INCLUDE[vstecado](../includes/vstecado-md.md)] mezi stránkou [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nebo jinou aplikací a databází [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Data obsahují počet a čas volání a maximální a minimální časy. Data interakce vrstev lze přidat mezi data profilace, která jsou shromážděna metodami vzorkování, instrumentace, paměti .NET nebo souběžnosti.  
  
 ![Data profilace interakce vrstev](../profiling/media/tierinteraction-profilingtools.png "TierInteraction_ProfilingTools")  
Data interakce vrstev, která jsou shromážděna nástroji pro profilaci  
  
 [Shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md)  
  
 [Zobrazení interakce vrstvy](../profiling/tier-interaction-views.md)  
  
## <a name="see-also"></a>Viz také  
 [Postupy: shromažďování údajů o výkonu webu](../profiling/how-to-collect-performance-data-for-a-web-site.md)   
 [Příručka pro začátečníky k profilaci výkonu](../profiling/beginners-guide-to-performance-profiling.md)
