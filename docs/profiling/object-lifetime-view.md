---
title: Zobrazení doby života objektu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 247c81d46ee8f5ae916a2a024620e4f4eb864194
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255616"
---
# <a name="object-lifetime-view"></a>Zobrazení doby života objektu
Doba života objektu zobrazení je k dispozici, když **taky shromažďovat životnosti objektů .NET** se kontroluje na **výkonnostní relace** stránky vlastností.  
  
 Uvolňování paměti z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] spravuje přidělování a uvolňování paměti pro vaši aplikaci. Za účelem optimalizace výkonu systému uvolňování spravovaná halda je rozdělené do tří generací: 0, 1 a 2. Uvolňování paměti modulu runtime ukládá nové objekty v 0. generace. Objekty, které zůstanou platné i po kolekce jsou povýší a uložené v generace 1 a 2.  
  
 Uvolňování paměti získá podle rušení přidělení celou generování objektů. Doba života objektu zobrazení pro objekty, které byly vytvořeny PROFILOVANÉHO aplikací, zobrazí počet a velikost objekty a generování, ve kterém se uvolní.  
  
## <a name="general"></a>Obecné  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název třídy**|Název třídy přidělené typu.|  
|**ID procesu**|ID procesu profilace spustit.|  
|**Název procesu**|Název procesu.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta modul, který obsahuje funkce.|  
  
## <a name="instance-data"></a>Instance data  
 Instance data označuje počet objektů typu, které byly vytvořeny v profilaci spustit a generování, ve kterém byly objekty navrácena modulem garbage collector.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Instance**|Počet přidělených objekty tohoto typu.|  
|**Celkový počet instancí %**|Procento z celkového počtu přidělení, které byly provedeny v profilaci spuštění.|  
|**Fin 0 instancí shromážděných**|Počet instancí typu, které byly při generování 0 algoritmus kolekce paměti navrácena.|  
|**Fin 1 instancí shromážděných**|Počet instancí typu, které byly navrácena v 1. generace kolekce algoritmu uvolňování paměti.|  
|**Fin 2 instance shromážděných**|Počet instancí typu, které byly navrácena v 2. generace kolekce algoritmu uvolňování paměti.|  
|**Instance zachování připojení na konci**|Počet instancí typu, které nebyly navrácena až do konce profilace spustit.|  
  
## <a name="size-byte-data"></a>Údaje o velikosti (v bajtech)  
 Velikost (v bajtech) dat určuje velikost objekty typu, které byly vytvořeny v profilaci spustit a množství paměti, která byla uvolnit v každé generování, ve kterém byly objekty navrácena.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celkový počet bajtů přidělených**|Celkový počet bajtů pro všechny instance typu.|  
|**Celkový počet bajtů %**|Procento celkový počet přidělených bajtů v profilaci spuštění, které byly přiděleny pro instance tohoto typu.|  
|**Fin 0 bajtů shromážděných**|Velikost instance typu, které byly při generování 0 algoritmus kolekce paměti navrácena.|  
|**Fin 1 bajtů, které jsou shromážděny**|Velikost instance typu, které byly navrácena v 1. generace kolekce algoritmu uvolňování paměti.|  
|**Fin 2 bajtů shromážděných**|Velikost instance typu, které byly navrácena v 2. generace kolekce algoritmu uvolňování paměti.|  
  
## <a name="large-object-heap-data"></a>Data rozsáhlého objektu haldy  
 Přidělení paměti .NET spravuje velmi rozsáhlých objektů v umístění, které je oddělené od standardní spravovaná halda. Data rozsáhlého objektu haldy označuje počet a velikost objekty typu spravovaných v tomto umístění.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Velkého objektu haldy instancí shromážděných**|Počet instancí tohoto typu, které se nacházely v haldě velkého objektu a které byly shromážděny v profilaci spustit.|  
|**Velkého objektu haldy bajtů shromážděných**|Velikost v bajtech instance tohoto typu, který se nacházely v haldě velkého objektu a které byly shromážděny v profilaci spustit.|  
  
## <a name="see-also"></a>Viz také:  
 [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)