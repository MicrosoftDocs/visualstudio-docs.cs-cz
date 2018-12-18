---
title: Shromažďování dat souběžnosti pro samostatné aplikace pomocí příkazového řádku Profiler | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc20cce20c07e4fe33cf343cd0cc900a46be5586
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789730"
---
# <a name="collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Shromažďování dat souběžnosti pro samostatné aplikace pomocí příkazového řádku profileru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za použití metody souběžnosti z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů pro profilaci sady umožňuje shromažďovat data kolize prostředků a data o činnosti vlákna, která ukazuje využití procesor, kolize vlákna, migrace vlákna, zpoždění synchronizace, oblasti překryté vstupně-výstupní operace a další systémové události.  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Spuštění rozhraní .NET Framework aplikace a profil dat souběžnosti**|-   [Postupy: spuštění aplikace rozhraní .NET Framework ke shromažďování dat souběžnosti](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Spuštění C/C++ aplikace a profil dat souběžnosti**|-   [Postupy: spuštění nativní aplikace za účelem shromáždění dat souběžnosti](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Připojení profileru k běžící aplikaci rozhraní .NET Framework**|-   [Postupy: připojení Profiler k aplikaci .NET Framework ke shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Připojení profileru k běžící aplikaci C/C++**|-   [Postupy: připojení Profiler k nativní aplikaci a shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Související úlohy  
  
### <a name="profiling-stand-alone-applications"></a>Profilace samostatných aplikací  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Profil s použitím metody vzorkování**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profil s použitím metody instrumentace**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Profilování paměti .NET přidělování a uvolňování paměti kolekce**|-   [Shromažďování dat paměti .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Přidání dat interakce vrstev**|-   [Shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profiling-concurrency-issues"></a>Profilace souběžnosti problémy  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Profil aplikace ASP.NET**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Profil služby**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analýza dat o souběžnosti zobrazeních a sestavách  
 [Zobrazení dat kolizí prostředku](../profiling/resource-contention-data-views.md)  
  
 [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Odkaz  
 [Referenční dokumentace nástrojů příkazového řádku pro profilaci](../profiling/command-line-profiling-tools-reference.md)



