---
title: Vytváření sestav profileru z příkazového řádku | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3433bef9b30c9b912d721b526ab11692a8de78af
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749268"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Vytváření sestav profileru z příkazového řádku
**Vsperfreport –** nástroj příkazového řádku lze vytvořit. *XML* nebo hodnot oddělených čárkami (. *CSV*) sestavy z dat profilaci (. *Vsp*) soubory. Typy sestav nástroje VSPerfReport přesně odpovídají zobrazením založeným na tabulkách rozhraní pro sadu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sestavu můžete filtrovat a zobrazit pouze váš kód a také zobrazit pouze část souboru dat profilování. Další informace najdete v tématu [vsperfreport –](../profiling/vsperfreport.md).  
  
 Můžete provést také datových souborů profilace usnadňují sdílet vložením symboly v. *vsp* soubory a pomocí vytváření předem analyzovaných sestavy (. *vsps*) soubory, které jsou menší a rychlejší otevřete.  
  
## <a name="common-tasks"></a>Běžné úlohy
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Vytvořte základní sestavu.** Vytvořte všechny nebo část typů sestav VSPerfReport.|-   [Vytváření základních sestav](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**Porovnejte dvě datových souborů profilování.** Vytvořte sestavu „diff“, která porovnává data o výkonu ve dvou souborech dat profilování.|-   [Postupy: vytvoření sestavy porovnání profileru z příkazového řádku](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Trasování volání zobrazení a data události trasování pro Windows (ETW).** Vytvořte sestavu trasování volání, která uvádí informace o časování pro jednotlivé body vstupu a výstupu funkcí aplikace a každé volání ostatních funkcí pomocí vaší funkce. Nebo vytvořte podrobný seznam všech událostí ETW, které byly shromážděny během spuštění profilování.|-   [Postupy: vytvoření sestavy trasování volání](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Filtrování sestavy.** Omezte sestavy pouze tyto funkce ve vašem kódu nebo v určený čas v profilaci datového souboru.|-   [Postupy: filtrování sestav z příkazového řádku](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Vytváření přenosných datových souborů profilování.** Chcete-li sdílení profilace data jednodušší, můžete vložit symboly pro profilaci k. *vsp* souboru. Můžete také vytvořit předem analyzovaných data profilování (. *vsps*) soubor, který je menší a rychlejší otevřete.|-   [Vytváření přenosných datových souborů profilace](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|