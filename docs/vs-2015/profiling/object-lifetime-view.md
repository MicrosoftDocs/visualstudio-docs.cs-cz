---
title: Zobrazení doby života objektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cc2e17084809e691838ea0e681e3d2b766d0769
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756434"
---
# <a name="object-lifetime-view"></a>Zobrazení doby života objektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení doby života objektu je k dispozici, když **také shromažďovat data o životním cyklu objektu .NET** proběhne na stránkách vlastností relace výkonu.  
  
 Ze systému uvolňování paměti [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] spravuje přidělování a uvolňování paměti pro vaši aplikaci. Za účelem optimalizace výkonu systému uvolňování paměti spravované haldy je rozdělen na tři generace: 0, 1 a 2. Uvolňování paměti modulu runtime uloží nové objekty 0. generace. Objekty, které byly zachovány při kolekce jsou povýšeny a uloženy v generace 1 a 2.  
  
 Získá systém uvolňování paměti podle rušení přidělení celé generace objektů. Pro objekty, které byly vytvořeny profilované aplikace zobrazení doba života objektu zobrazí počet a velikost objektů a generování, ve kterém se uvolní.  
  
## <a name="general"></a>Obecné  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název třídy**|Název třídy přiděleného typu.|  
|**ID procesu**|ID procesu spuštění profilování.|  
|**Název procesu**|Název procesu.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje funkci.|  
  
## <a name="instance-data"></a>Instance Data  
 Instance data označuje počet objektů typu, které byly vytvořeny v Profilování a jeho generaci, ve kterém byly objekty navrácena pomocí systému uvolňování paměti.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Instance**|Počet přidělení objektů tohoto typu.|  
|**% Instancí celkem**|Procento celkový počet přidělení, které byly provedeny v Profilování spuštění.|  
|**Shromážděné instance gen 0**|Číslo instance daného typu, které byly v algoritmu kolekce uvolnění paměti generace 0 navrácena.|  
|**Shromážděné instance Gen 1**|Číslo instance daného typu, které byly v 1. generace uvolňování paměti kolekce algoritmu navrácena.|  
|**Shromážděné instance Gen 2**|Číslo instance daného typu, které byly v 2. generace uvolňování paměti kolekce algoritmu navrácena.|  
|**Instance živé na konci**|Počet instance daného typu, které nebylo uvolnění až do konce profilace spuštěna.|  
  
## <a name="size-byte-data"></a>Údaje o velikosti (bajty)  
 Údaje o velikosti (bajty) označuje velikost objekty typu, které byly vytvořeny v Profilování a množství paměti, který byl uvolněn v každé generaci, ve kterém byly uvolnit objekty.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celkový počet přidělených bajtů**|Celkový počet bajtů pro všechny instance daného typu.|  
|**% Bajtů celkem**|Procento celkový počet přidělených bajtů při spuštění profilování, které byly přiděleny pro instance tohoto typu.|  
|**Shromážděné bajty gen 0**|Velikost instance daného typu, které byly v algoritmu kolekce uvolnění paměti generace 0 navrácena.|  
|**Shromážděné bajty Gen 1**|Velikost instance daného typu, které byly v 1. generace uvolňování paměti kolekce algoritmu navrácena.|  
|**Shromážděné bajty Gen 2**|Velikost instance daného typu, které byly v 2. generace uvolňování paměti kolekce algoritmu navrácena.|  
  
## <a name="large-object-heap-data"></a>Data haldy velkých objektů  
 Přidělení paměti .NET spravuje velmi velké objekty v umístění, které je oddělené od standardní spravované haldě. Data haldy velkých objektů označuje počet a velikost objektů typu, která se spravují v tomto umístění.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Shromážděné instance haldy velkých objektů**|Počet instancí tohoto typu, které se nacházely v haldy velkých objektů a, které byly shromážděny v profilaci spouštět.|  
|**Shromážděné bajty haldy velkých objektů**|Velikost v bajtech, instance tohoto typu, které se nacházely v haldy velkých objektů a, které byly shromážděny při spuštění profilace.|  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)



