---
title: Použití metod profilace ke shromažďování dat výkonu z příkazového řádku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d853322762942e874528b35164dc3f04a6c22b0a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722760"
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Použití metod profilace ke shromažďování dat výkonu z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podle vaší volby [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkazového řádku nástrojů pro profilaci a možnosti závisí na faktorech jako typ aplikace, který profilujete, metodě profilování, který chcete použít, a určuje, zda je cílová aplikace napsané v nativní nebo [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]kódu.  
  
 V tomto tématu jsou uspořádané příkazového řádku témat s postupy podle zvolené metodě profilování.  
  
## <a name="in-this-topic"></a>V tomto tématu  
 [Ke shromažďování statistik výkonu pomocí metody vzorkování](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Pomocí metody instrumentace ke shromažďování podrobných dat časování](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Pomocí metody paměti .NET ke shromažďování dat paměti přidělení a objekt životnosti](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Pomocí za použití metody souběžnosti ke shromažďování dat aktivity prostředku kolize a vlákna](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Přidání dat interakce vrstvy do běhu profilování](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Ke shromažďování statistik výkonu pomocí metody vzorkování  
 Metody nástroje pro profilaci vzorkování shromažďuje údaje o výkonu v pravidelných intervalech během spuštění profilování. Vzorkování dat může poskytnout přehled o problémy s výkonem vázané na procesor a může být dobrým způsobem, jak začít prozkoumávat výkon aplikace.  
  
 Můžete spustit profiler a aplikace ve stejnou dobu, nebo můžete připojení profileru k běžící instance aplikace.  
  
|Úloha|Typ cílové aplikace|  
|----------|-----------------------------|  
|**Spuštění aplikace**|-   [Samostatné aplikace](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Připojit ke spuštěnému procesu**|-   [Samostatné aplikace rozhraní .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Nativní samostatné aplikace](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Webové aplikace ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Služby rozhraní .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Nativní služby](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Pomocí metody instrumentace ke shromažďování podrobných dat časování  
 Metody nástroje pro profilaci instrumentace shromažďuje údaje o výkonu z kopie binární soubory aplikace, které obsahují software sondy, informace o záznamu výkonu. Na začátek a konec jednotlivých instrumentované funkcí a při každém volání dalších funkcí z instrumentované funkce se shromažďují data instrumentace. Metody instrumentace je užitečná při odhalování problémů s výkonem pomocí problémy vstupně-výstupních operací, jako je využití místa na disku.  
  
 Vytvoření instrumentovaný binární soubor s [VInstr.exe](../profiling/vsinstr.md) nástroj. Po inicializaci profileru, data se automaticky shromažďují z instrumentované binární soubory při spuštění cílové aplikace.  
  
 **Typ cílové aplikace**  
  
-   [Samostatné součásti rozhraní .NET framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Nativní samostatné součásti](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Staticky kompilované webové aplikace ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [Dynamicky kompilovaných webových aplikací ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [Služby rozhraní .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Nativní služby](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Pomocí metody paměti .NET ke shromažďování dat paměti přidělení a objekt životnosti  
 Metoda paměti .NET nástrojů pro profilaci umožňuje shromažďovat [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] data o přidělování paměti a informace o životnosti objektů v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 Můžete spustit cílovou aplikaci pomocí profileru; můžete připojení profileru k běžící instance aplikace. a můžete vytvořit instrumentované verze této aplikace ke shromažďování podrobných informací o časování spolu s [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] data paměti.  
  
|Úloha|Typ cílové aplikace|  
|----------|-----------------------------|  
|**Spuštění aplikace**|-   [Aplikace samostatné rozhraní .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Připojit ke spuštěnému procesu**|-   [Samostatné aplikace rozhraní .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Webové aplikace ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Služby rozhraní .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Nástroj moduly**|-   [Samostatné součásti rozhraní .NET framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Staticky kompilované webové aplikace ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Dynamicky kompilovaných webových aplikací ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Služby rozhraní .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Pomocí za použití metody souběžnosti ke shromažďování dat aktivity prostředku kolize a vlákna  
 Za použití metody souběžnosti nástrojů pro profilaci sady umožňuje shromažďovat kolize prostředků a dat aktivit vláken a procesů z aplikací s více vlákny.  
  
 Aplikaci můžete spustit pomocí profileru, nebo můžete připojení profileru k běžící instance aplikace.  
  
|Úloha|Typ cílové aplikace|  
|----------|-----------------------------|  
|**Spuštění aplikace**|-   [Samostatné rozhraní .NET Framework aplikace](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Samostatné nativní aplikace](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Připojit ke spuštěnému procesu**|-   [Samostatné aplikace rozhraní .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Nativní samostatné aplikaci](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Webová aplikace ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Služby rozhraní .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Nativní služby](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Přidání dat interakce vrstvy do běhu profilování  
 Přidání dat interakce vrstvy do běhu profilování vyžaduje zvláštní procedury s nástroji pro profilaci příkazového řádku. Zobrazit [shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Viz také  
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)



