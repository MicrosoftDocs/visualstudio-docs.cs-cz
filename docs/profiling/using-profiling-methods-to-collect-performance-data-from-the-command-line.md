---
title: Použití metod profilace z příkazového řádku k získání údajů o výkonu
description: Zjistěte, jak volba nástrojů a nástrojů příkazového řádku sady Visual Studio Nástroje pro profilaci, závisí na faktorech, jako je typ aplikace, kterou vytváříte profilování.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1796fad03d04ffb79ca1c8aeccc241ee3698f9f1
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723241"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Použití metod profilace ke shromažďování dat výkonu z příkazového řádku
Vaše volba [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci nástrojů a možností příkazového řádku závisí na faktorech, jako je typ aplikace, kterou vytváříte profilování, metodu profilace, kterou chcete použít, a zda je cílová aplikace napsána v nativním nebo .NET Frameworkm kódu.

 Toto téma uspořádá procedurální témata příkazového řádku podle vámi zvolené metody profilace.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Shromažďování statistik výkonu pomocí metody vzorkování
 Metoda vzorkování Nástroje pro profilaci shromažďuje údaje o výkonu v zadaných intervalech při spuštění profilace. Vzorkování dat může poskytovat přehled o problémech s výkonem vázaných na procesor a může být dobrým způsobem, jak začít zkoumat výkon aplikace.

 Můžete spustit Profiler a aplikaci ve stejnou dobu, nebo můžete připojit profiler ke spuštěné instanci aplikace.

|Úkol|Typ cílové aplikace|
|----------|-----------------------------|
|**Spuštění aplikace**|-   [Samostatné aplikace](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Připojit ke spuštěnému procesu**|-   [.NET Framework samostatné aplikace](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Nativní samostatné aplikace](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [Webové aplikace v ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Služby .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Nativní služby](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Shromažďování podrobných dat časování pomocí metody instrumentace
 Metoda instrumentace Nástroje pro profilaci shromažďuje údaje o výkonu z kopií binárních souborů aplikace, které obsahují sondy softwaru pro zaznamenávání informací o výkonu. Data instrumentace se shromažďují na začátku a konci každé instrumentované funkce a při každém volání dalších funkcí z instrumentované funkce. Metoda instrumentace je užitečná při zjišťování problémů s výkonem při vstupně-výstupních potížích, jako je například využití disku.

 Pomocí nástroje [VInstr.exe](../profiling/vsinstr.md) vytvoříte instrumentované binární soubory. Po inicializaci profileru se data automaticky shromažďují z instrumentované binárních souborů při spuštění cílové aplikace.

 **Typ cílové aplikace**

- [.NET Framework samostatné součásti](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [Nativní samostatné součásti](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [Staticky kompilované webové aplikace ASP.NET](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [Dynamicky kompilované webové aplikace v ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [Služby .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [Nativní služby](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Pomocí metod paměti .NET Shromážděte data o přidělení paměti a životnosti objektů.
 Metoda Nástroje pro profilaci paměti .NET umožňuje shromažďovat .NET Framework data o přidělování paměti a informace o životnosti objektů v .NET Framework.

 Cílovou aplikaci můžete spustit pomocí profileru. Profiler můžete připojit ke spuštěné instanci aplikace. a můžete vytvořit instrumentované verze aplikace pro shromažďování podrobných informací o časování spolu s daty .NET Framework paměti.

|Úkol|Typ cílové aplikace|
|----------|-----------------------------|
|**Spuštění aplikace**|-   [Samostatné .NET Framework aplikace](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**Připojit ke spuštěnému procesu**|-   [.NET Framework samostatné aplikace](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [Webové aplikace v ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Služby .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**Moduly instrumentace**|-   [.NET Framework samostatné součásti](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Staticky kompilované webové aplikace ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Dynamicky kompilované webové aplikace v ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [Služby .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Použití metody souběžnosti ke shromažďování dat o kolize prostředků a aktivitách vláken
 Metoda Nástroje pro profilaci souběžnosti umožňuje shromažďovat data o kolize prostředků a vláknech a zpracovávat data aktivit z vícevláknových aplikací.

 Aplikaci můžete spustit pomocí profileru nebo můžete připojit profiler ke spuštěné instanci aplikace.

|Úkol|Typ cílové aplikace|
|----------|-----------------------------|
|**Spuštění aplikace**|-   [Samostatná .NET Framework aplikace](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Samostatná nativní aplikace](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Připojit ke spuštěnému procesu**|-   [.NET Framework samostatné aplikace](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Nativní samostatná aplikace](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [Webová aplikace ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Služba .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Nativní služba](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Přidání dat interakce vrstev do běhu profilace
 Přidání dat interakce vrstev do běhu profilování vyžaduje konkrétní procedury s nástroji pro profilaci příkazového řádku. Viz [shromáždění dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md) .

## <a name="see-also"></a>Viz také
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
