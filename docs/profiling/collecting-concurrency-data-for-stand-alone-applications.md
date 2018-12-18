---
title: Shromažďování dat souběžnosti pro samostatné aplikace pomocí příkazového řádku Profiler | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7966bcffff03c23b99837ba69f591d76258146c
ms.sourcegitcommit: 4400926d00b5f5d52f03cb5d6f8a582d6049ecd9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2018
ms.locfileid: "39276478"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Shromažďování dat souběžnosti pro samostatné aplikace pomocí příkazového řádku profileru
Za použití metody souběžnosti z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástrojů pro profilaci sady umožňuje shromažďovat data kolize prostředků a data o činnosti vlákna, která ukazuje využití procesor, kolize vlákna, migrace vlákna, zpoždění synchronizace, oblasti překryté vstupně-výstupní operace a další systémové události.  
  

## <a name="common-tasks"></a>Běžné úlohy  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Spuštění rozhraní .NET Framework aplikace a profil dat souběžnosti**|-   [Postupy: spuštění aplikace rozhraní .NET Framework ke shromažďování dat souběžnosti](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|  
|**Spuštění C/C++ aplikace a profil dat souběžnosti**|-   [Postupy: spuštění nativní aplikace za účelem shromáždění dat souběžnosti](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|  
|**Připojení profileru k běžící aplikaci rozhraní .NET Framework**|-   [Postupy: připojení profileru k aplikaci rozhraní .NET Framework ke shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|  
|**Připojení profileru k běžící aplikaci C/C++**|-   [Postupy: připojení profileru k nativní aplikaci a shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|  
  
## <a name="related-tasks"></a>Související úlohy
  
### <a name="profile-stand-alone-applications"></a>Samostatné aplikace profilu  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Profil s použitím metody vzorkování**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|  
|**Profil s použitím metody instrumentace**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**Profilování paměti .NET přidělování a uvolňování paměti kolekce**|-   [Shromažďování dat paměti .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**Přidání dat interakce vrstev**|-   [Shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profile-concurrency-issues"></a>Potíže se souběžností profilu  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Profil aplikace ASP.NET**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
|**Profil služby**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyze-concurrency-data-views-and-reports"></a>Analýza souběžnosti zobrazení dat a sestav  
 [Zobrazení dat kolizí prostředku](../profiling/resource-contention-data-views.md)  
  
 [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Odkaz  
 [Referenční dokumentace nástrojů příkazového řádku pro profilaci](../profiling/command-line-profiling-tools-reference.md)