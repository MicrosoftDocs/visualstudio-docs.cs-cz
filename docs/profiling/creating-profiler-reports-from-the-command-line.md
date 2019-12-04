---
title: Vytváření sestav profileru z příkazového řádku | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777774"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Vytváření sestav profileru z příkazového řádku
Nástroj příkazového řádku **VSPerfReport** umožňuje vytvořit. *XML* nebo hodnota oddělená čárkou (. *CSV*) sestavy z dat profilace (. *VSP*) soubory. Typy sestav nástroje VSPerfReport přesně odpovídají zobrazením založeným na tabulkách rozhraní pro sadu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sestavu můžete filtrovat a zobrazit pouze váš kód a také zobrazit pouze část souboru dat profilování. Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md).

 Můžete také usnadnit sdílení datových souborů profilování vložením symbolů do. soubory *VSP* a vytvořením předem analyzované sestavy (. *vsps*) menší a rychlejší otevírání souborů.

## <a name="common-tasks"></a>Běžné úlohy

|Úloha|Související obsah|
|----------|---------------------|
|**Vytvoří základní sestavu.** Vytvořte všechny nebo část typů sestav VSPerfReport.|-   [vytváření základních sestav](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**Porovná dva soubory dat profilování.** Vytvořte sestavu „diff“, která porovnává data o výkonu ve dvou souborech dat profilování.|-   [Postupy: Vytvoření sestavy porovnání profileru z příkazového řádku](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**Zobrazit trasování volání a data trasování událostí pro Windows (ETW).** Vytvořte sestavu trasování volání, která uvádí informace o časování pro jednotlivé body vstupu a výstupu funkcí aplikace a každé volání ostatních funkcí pomocí vaší funkce. Nebo vytvořte podrobný seznam všech událostí ETW, které byly shromážděny během spuštění profilování.|-   [Postupy: Vytvoření sestavy trasování volání](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**Filtruje sestavu.** Omezte sestavu jenom na funkce v kódu nebo na určitou dobu v souboru dat profilování.|-   [Postupy: filtrování sestav z příkazového řádku](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**Vytváření přenosných datových souborů profilace.** Aby bylo sdílení dat profilace snazší, můžete vložit symboly pro spuštění profilování do. soubor *VSP* . Můžete také vytvořit předem Analyzovaná data profilace (. *vsps*), který je menší a rychlejší, aby se otevřel.|-   [vytváření přenosných datových souborů profilace](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
