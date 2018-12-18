---
title: Shromažďování statistik aplikace pro samostatné aplikace pomocí příkazového řádku Profiler | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72efb2481725d7e0da9331b639040d7dacc8298d
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276728"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Shromažďování statistik aplikace pro samostatné aplikace pomocí příkazového řádku profileru
Tato část popisuje postupy a možnosti pro shromažďování statistik výkonu pro klientskou aplikaci (samostatný) pomocí metody vzorkování z příkazového řádku.  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Běžné úlohy  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Spusťte aplikaci pomocí profilace**|-   [Postupy: spuštění samostatné aplikace a shromažďování statistik aplikace](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|  
|**Připojení profileru k běžící aplikaci rozhraní .NET Framework**|-   [Postupy: připojení profileru k aplikaci .NET Framework a shromažďování statistik aplikace](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|  
|**Připojení profileru k běžící aplikaci C/C++**|-   [Postupy: připojení profileru k nativní aplikaci a shromažďování statistik aplikace](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|  
|**Přidání dat interakce vrstev**|-   [Shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Související úlohy  
  
### <a name="profile-stand-alone-applications"></a>Samostatné aplikace profilu  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Instrumentovat aplikaci**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**Shromažďování dat paměti .NET přidělování a uvolňování paměti kolekce**|-   [Shromažďování dat paměti .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**Shromažďování dat prostředku kolize a vlákno provádění**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|  
  
### <a name="profile-by-using-the-sampling-method"></a>Profil s použitím metody vzorkování  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Webové aplikace ASP.NET profilu**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|  
|**Profil služby**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Popisuje, jak shromáždit statistiky výkonu ze služby Windows s použitím metody vzorkování.|  
  
### <a name="analyze-sampling-data-views-and-reports"></a>Analýza zobrazení dat vzorkování a sestavy  
 [Zobrazení dat metod vzorkování](../profiling/profiler-sampling-method-data-views.md)

