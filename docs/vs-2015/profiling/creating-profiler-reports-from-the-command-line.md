---
title: Vytváření sestav profileru z příkazového řádku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 489ebd4e5aff3ef9b93ef0d8fe18f9ae8cc85011
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537199"
---
# <a name="creating-profiler-reports-from-the-command-line"></a>Vytváření sestav profileru z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj příkazového řádku **VSPerfReport** umožňuje vytvořit sestavy hodnot (. csv) s oddělovači (. csv) ze souborů dat profilování (. vsp). Typy sestav nástroje VSPerfReport přesně odpovídají zobrazením založeným na tabulkách rozhraní pro sadu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sestavu můžete filtrovat a zobrazit pouze váš kód a také zobrazit pouze část souboru dat profilování. Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md).  
  
 Soubory dat profilování lze také jednodušeji sdílet vložením symbolů do souboru .vsp a vytvořením předem analyzovaných souborů sestav (.vsps), které jsou menší a rychleji se otevírají.  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|Úkol|Související obsah|  
|----------|---------------------|  
|**Vytvoří základní sestavu.** Vytvořte všechny nebo část typů sestav VSPerfReport.|-   [Vytváření základních sestav](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**Porovná dva soubory dat profilování.** Vytvořte sestavu „diff“, která porovnává data o výkonu ve dvou souborech dat profilování.|-   [Postupy: Vytvoření sestavy porovnání profileru z příkazového řádku](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Zobrazit trasování volání a data trasování událostí pro Windows (ETW).** Vytvořte sestavu trasování volání, která uvádí informace o časování pro jednotlivé body vstupu a výstupu funkcí aplikace a každé volání ostatních funkcí pomocí vaší funkce. Nebo vytvořte podrobný seznam všech událostí ETW, které byly shromážděny během spuštění profilování.|-   [Postupy: Vytvoření sestavy trasování volání](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Filtruje sestavu.** Omezte sestavu jenom na funkce v kódu nebo na určitou dobu v souboru dat profilování.|-   [Postupy: filtrování sestav z příkazového řádku](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Vytváření přenosných datových souborů profilace.** Chcete-li sdílet data profilování snadněji, lze vložit symboly pro běh profilování do souboru .vsp. Můžete také vytvořit předem analyzovaný soubor dat profilování (.vsps), který je menší a lze jej rychleji otevřít.|-   [Vytváření přenosných datových souborů profilace](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
