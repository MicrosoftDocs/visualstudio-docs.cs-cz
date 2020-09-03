---
title: Nástroje pro profilaci pravidla použití | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4158a6a393ed6e64dedddfca10c1ae04a95e3d3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535548"
---
# <a name="profiling-tools-usage-rules"></a>Pravidla používání nástrojů pro profilaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pravidla výkonu v kategorii použití Nástroje pro profilaci poskytují pokyny pro použití profileru pro efektivní shromažďování dat.  
  
|Pravidlo|Popis|  
|-|-|  
|[DA0002: Chybí knihovna VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|Profilace příkazového řádku může obsahovat nekompletní data pro [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] binární soubory. To může být způsobeno tím, že nenastavuje správné proměnné prostředí.|  
|[DA0003: Velký počet vzorků jádra](../profiling/da0003-many-kernel-samples.md)|Bylo zaznamenáno mnoho ukázek profilace, k nimž došlo mimo provádění cílového binárního souboru. Chcete-li shromáždit přesnější data, zvažte použití metody instrumentace.|  
|[DA0004: Vysoké využití procesoru](../profiling/da0004-high-processor-usage.md)|Data profilování naznačují, že vaše procesory byly během spuštění profilace konzistentně zaneprázdněné. Chcete-li shromáždit přesnější data, zvažte použití metody vzorkování.|  
|[DA0008: Shromážděno málo vzorků](../profiling/da0008-few-samples-collected.md)|Počet vzorků shromážděných při spuštění profilování nebyl dostatečně vysoký, aby byl statisticky významný. Zvažte opětovné vytvoření profilování a spuštění aplikace po delší dobu. Můžete také zvážit použití metody instrumentace ke shromažďování dat.|  
|[DA0026: Nadměrný čas zpracování procesoru jádra](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|V režimu jádra procesoru došlo k výraznému času při spuštění profilace. Zvažte vzorkování pomocí systémových volání jako metriky namísto použití času jako metriky.|  
|[DA0029: Nepodporovaná verze CLR](../profiling/da0029-unsupported-clr-version.md)|Profilované binární soubory používají verzi nástroje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , která není podporována profilerem. Sestavy profileru nemůžou přeložit názvy symbolů.|  
|[DA0030: Získání měření interakce vrstev pro databázové projekty](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Shromáždil se značný počet volání metod v <xref:System.Data?displayProperty=fullName> oboru názvů. Pokud chcete zahrnout data o voláních databáze, zvažte shromáždění dat interakce vrstev ve vašem profilu.|
