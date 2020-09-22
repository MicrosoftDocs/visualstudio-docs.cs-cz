---
title: Profilace příkazového řádku – vytváření sestav
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5eb0f1fa0f9bbe760b1ea89074d02044cf26ab7d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808822"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Vytváření sestav profileru z příkazového řádku
Nástroj příkazového řádku **VSPerfReport** umožňuje vytvořit. *XML* nebo hodnota oddělená čárkou (.* CSV*) sestavy z dat profilace (.* VSP*) soubory. Typy sestav nástroje VSPerfReport přesně odpovídají zobrazením založeným na tabulkách rozhraní pro sadu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sestavu můžete filtrovat a zobrazit pouze váš kód a také zobrazit pouze část souboru dat profilování. Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md).

 Můžete také usnadnit sdílení datových souborů profilování vložením symbolů do. soubory *VSP* a vytvořením předem analyzované sestavy (.* vsps*) menší a rychlejší otevírání souborů.

## <a name="common-tasks"></a>Běžné úkoly

|Úloha|Související obsah|
|----------|---------------------|
|**Vytvoří základní sestavu.** Vytvořte všechny nebo část typů sestav VSPerfReport.|-   [Vytvoření základních sestav](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**Porovná dva soubory dat profilování.** Vytvořte sestavu „diff“, která porovnává data o výkonu ve dvou souborech dat profilování.|-   [Postupy: Vytvoření sestavy porovnání profileru z příkazového řádku](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**Zobrazit trasování volání a data trasování událostí pro Windows (ETW).** Vytvořte sestavu trasování volání, která uvádí informace o časování pro jednotlivé body vstupu a výstupu funkcí aplikace a každé volání ostatních funkcí pomocí vaší funkce. Nebo vytvořte podrobný seznam všech událostí ETW, které byly shromážděny během spuštění profilování.|-   [Postupy: Vytvoření sestavy trasování volání](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**Filtruje sestavu.** Omezte sestavu jenom na funkce v kódu nebo na určitou dobu v souboru dat profilování.|-   [Postupy: filtrování sestav z příkazového řádku](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**Vytváření přenosných datových souborů profilace.** Aby bylo sdílení dat profilace snazší, můžete vložit symboly pro spuštění profilování do. soubor *VSP* . Můžete také vytvořit předem Analyzovaná data profilace (.* vsps*), který je menší a rychlejší, aby se otevřel.|-   [Vytváření přenosných datových souborů profilace](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
