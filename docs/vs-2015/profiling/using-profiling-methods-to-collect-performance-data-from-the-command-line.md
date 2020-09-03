---
title: Použití metod profilace ke shromažďování dat výkonu z příkazového řádku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fe9e8d3dbd1e7395287cd7241f1e6145dffca7e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145400"
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Použití metod profilace ke shromažďování dat výkonu z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vaše volba [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci nástrojů a možností příkazového řádku závisí na faktorech, jako je typ aplikace, kterou vytváříte profilování, metodu profilace, kterou chcete použít, a zda je cílová aplikace napsána v nativním kódu nebo v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] kódu.  
  
 Toto téma uspořádá procedurální témata příkazového řádku podle vámi zvolené metody profilace.  
  
## <a name="in-this-topic"></a>V tomto tématu  
 [Shromažďování statistik výkonu pomocí metody vzorkování](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Shromažďování podrobných dat časování pomocí metody instrumentace](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Použití metod paměti .NET ke shromažďování dat o přidělení paměti a životnosti objektů](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Použití metody Concurrency ke shromažďování dat o kolize prostředků a aktivitách vláken](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Přidání dat interakce vrstev do běhu profilace](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
## <a name="using-the-sampling-method-to-collect-performance-statistics"></a><a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Shromažďování statistik výkonu pomocí metody vzorkování  
 Metoda vzorkování Nástroje pro profilaci shromažďuje údaje o výkonu v zadaných intervalech při spuštění profilace. Vzorkování dat může poskytovat přehled o problémech s výkonem vázaných na procesor a může být dobrým způsobem, jak začít zkoumat výkon aplikace.  
  
 Můžete spustit Profiler a aplikaci ve stejnou dobu, nebo můžete připojit profiler ke spuštěné instanci aplikace.  
  
|Úkol|Typ cílové aplikace|  
|----------|-----------------------------|  
|**Spuštění aplikace**|-   [Samostatné aplikace](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Připojit ke spuštěnému procesu**|-   [.NET Framework samostatné aplikace](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Nativní samostatné aplikace](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Webové aplikace v ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Služby .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Nativní služby](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="using-the-instrumentation-method-to-collect-detailed-timing-data"></a><a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Shromažďování podrobných dat časování pomocí metody instrumentace  
 Metoda instrumentace Nástroje pro profilaci shromažďuje údaje o výkonu z kopií binárních souborů aplikace, které obsahují sondy softwaru pro zaznamenávání informací o výkonu. Data instrumentace se shromažďují na začátku a konci každé instrumentované funkce a při každém volání dalších funkcí z instrumentované funkce. Metoda instrumentace je užitečná při zjišťování problémů s výkonem při vstupně-výstupních potížích, jako je například využití disku.  
  
 Pomocí nástroje [VInstr.exe](../profiling/vsinstr.md) vytvoříte instrumentované binární soubory. Po inicializaci profileru se data automaticky shromažďují z instrumentované binárních souborů při spuštění cílové aplikace.  
  
 **Typ cílové aplikace**  
  
- [.NET Framework samostatné součásti](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
- [Nativní samostatné součásti](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
- [Staticky kompilované webové aplikace ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
- [Dynamicky kompilované webové aplikace v ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
- [Služby .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
- [Nativní služby](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
## <a name="using-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a><a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Použití metod paměti .NET ke shromažďování dat o přidělení paměti a životnosti objektů  
 Metoda Nástroje pro profilaci paměti .NET umožňuje shromažďovat [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] data o přidělování paměti a informace o životnosti objektů v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 Cílovou aplikaci můžete spustit pomocí profileru. Profiler můžete připojit ke spuštěné instanci aplikace. a můžete vytvořit instrumentované verze aplikace pro shromažďování podrobných informací o časování spolu s [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] daty paměti.  
  
|Úkol|Typ cílové aplikace|  
|----------|-----------------------------|  
|**Spuštění aplikace**|-   [Samostatné .NET Framework aplikace](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Připojit ke spuštěnému procesu**|-   [.NET Framework samostatné aplikace](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Webové aplikace v ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Služby .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Moduly instrumentace**|-   [.NET Framework samostatné součásti](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Staticky kompilované webové aplikace ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Dynamicky kompilované webové aplikace v ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Služby .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="using-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a><a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Použití metody Concurrency ke shromažďování dat o kolize prostředků a aktivitách vláken  
 Metoda Nástroje pro profilaci souběžnosti umožňuje shromažďovat data o kolize prostředků a vláknech a zpracovávat data aktivit z vícevláknových aplikací.  
  
 Aplikaci můžete spustit pomocí profileru nebo můžete připojit profiler ke spuštěné instanci aplikace.  
  
|Úkol|Typ cílové aplikace|  
|----------|-----------------------------|  
|**Spuštění aplikace**|-   [Samostatná .NET Framework aplikace](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Samostatná nativní aplikace](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Připojit ke spuštěnému procesu**|-   [.NET Framework samostatné aplikace](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Nativní samostatná aplikace](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)<br />-   [Webová aplikace ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Služba .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Nativní služba](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="adding-tier-interaction-data-to-a-profiling-run"></a><a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Přidání dat interakce vrstev do běhu profilace  
 Přidání dat interakce vrstev do běhu profilování vyžaduje konkrétní procedury s nástroji pro profilaci příkazového řádku. Viz [shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Viz také  
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
