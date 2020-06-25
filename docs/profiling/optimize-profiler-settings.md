---
title: Optimalizují se nastavení profileru | Microsoft Docs
ms.date: 4/29/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiler, improve performance
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9ff76364026230d08d03c91d14bddba3c325e7be
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290408"
---
# <a name="optimizing-profiler-settings"></a>Optimalizace nastavení profileru

Profiler výkonu a Diagnostické nástroje okno v aplikaci Visual Studio mají mnoho různých nastavení, která mají vliv na celkový výkon nástrojů. Změna některých nastavení může způsobit, že se analýza spustí rychle nebo když se v nástrojích vymění další čekací doby. Níže je souhrn určitých nastavení a jejich dopad na výkon.

## <a name="symbol-settings"></a>Nastavení symbolu

Nastavení symbolů v možnostech ladicího programu (**možnosti ladění > > symboly**) mají výrazný dopad na to, jak dlouho trvá generování výsledků v nástrojích. Když povolíte servery symbolů nebo pomocí **_NT_SYMBOL_PATH** způsobí, že Profiler vyžádá symboly pro každý načtený modul v sestavě. V současné době Profiler vždy automaticky načte všechny symboly bez ohledu na automatickou předvolbu automatického načítání symbolů.

![Stránka načítání symbolů](../profiling/media/symbolloading.png "Načítání symbolů")

Průběh načítání symbolů lze zobrazit v okně **výstup** pod nadpisem **diagnostické nástroje** .

![Průběh načítání symbolů](../profiling/media/symbolloadingprogress.png "Průběh načítání symbolů")

Po stažení se symboly ukládají do mezipaměti, které budou zrychlit budoucí analýzu, ale stále vyžadují načítání a analýzu souborů. Pokud načítání symbolů zpomaluje analýzu, zkuste vypnout servery symbolů a vymažte mezipaměť symbolů. Místo toho se spoléhá na symboly sestavené místně pro váš projekt.

## <a name="show-external-code"></a>Zobrazit externí kód

Mnohé z nástrojů v **profileru výkonu** a v **diagnostické nástroje** okně mají koncept uživatelského kódu vs External Code. Uživatelský kód je jakýkoli kód, který je sestaven otevřeným řešením nebo otevřeným pracovním prostorem. Externí kód je cokoli jiného. Když zachováte nastavení **Zobrazit externí kód** jako zakázané nebo chcete **Zobrazit možnost pouze můj kód** , umožníte nástrojům agregovat externí kód do jediného rámce na první úrovni, což významně snižuje množství zpracování, které je nutné k zobrazení výsledků. To umožňuje uživatelům zobrazit, co bylo voláno v externím kódu, který zpomaluje zpracování a udržuje data na minimum. Pokud je to možné, nechejte **Zobrazit externí kód** zakázaný a ujistěte se, že máte otevřené řešení nebo pracovní prostor pro diagsession, které analyzujete.

## <a name="trace-duration"></a>Doba trvání trasování

Profilace menších dob trvání má za následek méně dat, což je rychlejší analýza. Obvykle doporučujeme, abyste si vyzkoušeli, že vaše trasování nebudou mít data o výkonu déle než pět minut. Některé nástroje, jako je například nástroj [využití CPU](../profiling/cpu-usage.md) , umožňují pozastavit shromažďování dat v době, kdy je nástroj spuštěný, abyste mohli omezit množství shromažďovaných dat ke scénáři, který vás zajímá při analýze.

## <a name="sampling-frequency"></a>Frekvence vzorkování

Některé nástroje, například nástroj [využití CPU](../profiling/cpu-usage.md) a nástroj pro [přidělování objektů](../profiling/dotnet-alloc-tool.md) , umožňují upravit četnost vzorkování. Zvýšení této frekvence vzorkování vám umožní přesněji změřit, ale zvyšuje množství dat, která se generují. Obvykle je vhodné ponechat toto nastavení výchozí sazbou, pokud se konkrétní problém nezkoumá.

![Stránka vlastností centrálního centra diagnostiky](../profiling/media/diaghubpropertiespage.png "Stránka vlastností centrálního centra diagnostiky")

## <a name="see-also"></a>Viz také

- [Spuštění nástrojů pro profilaci s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Současné použití více nástrojů profileru](../profiling/use-multiple-profiler-tools-simultaneously.md)
- [Porozumění metodám shromažďování údajů o výkonu](../profiling/understanding-performance-collection-methods-perf-profiler.md)
