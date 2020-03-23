---
title: Vytváření sestav profileru z příkazového řádku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7f28d7271fdf33822475a663debed269bb515959
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777774"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Vytvoření sestav profileru z příkazového řádku
Nástroj příkazového řádku **VSPerfReport** umožňuje vytvářet . xml *nebo* čárka-oddělené hodnoty (.* csv*) sestavy z profilovacích dat (.* vsp*) soubory. Typy sestav nástroje VSPerfReport přesně odpovídají zobrazením založeným na tabulkách rozhraní pro sadu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sestavu můžete filtrovat a zobrazit pouze váš kód a také zobrazit pouze část souboru dat profilování. Další informace naleznete [v tématu VSPerfReport](../profiling/vsperfreport.md).

 Můžete také usnadnit sdílení datových souborů profilování vložením symbolů do . *vsp* a vytvořením předem analyzované sestavy (.* vsps*) soubory, které jsou menší a rychlejší otevřít.

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Vytvořte základní sestavu.** Vytvořte všechny nebo část typů sestav VSPerfReport.|-   [Vytváření základních sestav](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**Porovnejte dva datové soubory profilování.** Vytvořte sestavu „diff“, která porovnává data o výkonu ve dvou souborech dat profilování.|-   [Postup: Vytvoření sestavy porovnání profileru z příkazového řádku](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**Zobrazení trasování volání a trasování událostí pro data systému Windows (ETW).** Vytvořte sestavu trasování volání, která uvádí informace o časování pro jednotlivé body vstupu a výstupu funkcí aplikace a každé volání ostatních funkcí pomocí vaší funkce. Nebo vytvořte podrobný seznam všech událostí ETW, které byly shromážděny během spuštění profilování.|-   [Postup: Vytvoření sestavy trasování hovorů](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**Filtrovat sestavu.** Omezte sestavu pouze na funkce v kódu nebo na určitý čas v datovém souboru profilování.|-   [Postup: Filtrování sestav z příkazového řádku](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**Vytvořte přenosné profilovací datové soubory.** Chcete-li usnadnit sdílení dat profilování, můžete vložit symboly pro profilování spustit do . *vsp.* Můžete také vytvořit předem analyzovaná data profilování (.* vsps*) soubor, který je menší a rychlejší otevřít.|-   [Vytvoření přenosných datových souborů profilování](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
