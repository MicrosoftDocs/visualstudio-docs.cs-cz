---
title: Použití metod profilování příkazového řádku k získání dat o výkonu
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b30aa723ea3014aec2bd05d4bd204b9427b3c218
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779971"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Použití metod profilace ke shromažďování dat výkonu z příkazového řádku
Výběr nástrojů [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a možností příkazového řádku Nástroje profilování závisí na faktorech, jako je typ aplikace, kterou profilujete, metodu profilování, kterou chcete použít, a na tom, zda je cílová aplikace zapsána v nativním kódu nebo kódu rozhraní .NET Framework.

 Toto téma uspořádá procedurální témata příkazového řádku podle zvolené metody profilování.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Pomocí metody odběru vzorků můžete shromažďovat statistiky výkonu.
 Metoda vzorkování profilovacích nástrojů shromažďuje data o výkonu v určených intervalech při spuštění profilování. Vzorkování dat může poskytnout přehled o problémech s výkonem vázané na procesor a může být dobrý způsob, jak začít zkoumat výkon aplikace.

 Můžete spustit profiler a aplikace současně, nebo můžete připojit profiler ke spuštěné instanci aplikace.

|Úkol|Cílový typ aplikace|
|----------|-----------------------------|
|**Spuštění aplikace**|-   [Samostatné aplikace](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Připojení ke spuštěnému procesu**|-   [Samostatné aplikace rozhraní .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Nativní samostatné aplikace](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [ASP.NET webových aplikací](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Služby .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Nativní služby](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Použití metody instrumentace ke shromažďování podrobných časových dat
 Metoda instrumentace profilovacích nástrojů shromažďuje data o výkonu z kopií binárních souborů aplikace, které obsahují softwarové sondy pro záznam informací o výkonu. Instrumentační data jsou shromažďována na začátku a na konci každé instrumentované funkce a při každém volání na další funkce z instrumentované funkce. Metoda instrumentace je užitečná pro zjišťování problémů s výkonem vstupně-va problémy, jako je například využití disku.

 Instrumentované binární soubory vytvoříte pomocí nástroje [VInstr.exe.](../profiling/vsinstr.md) Po inicializaci profileru jsou data automaticky shromažďována z instrumentovaných binárních souborů při spuštění cílové aplikace.

 **Cílový typ aplikace**

- [Samostatné součásti rozhraní .NET Framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [Nativní samostatné součásti](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [Staticky kompilované ASP.NET webových aplikací](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [Dynamicky kompilované ASP.NET webových aplikací](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [Služby .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [Nativní služby](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Použití metod paměti .NET ke shromažďování dat přidělení paměti a životnosti objektu
 Metoda paměťové nástroje profilování .NET umožňuje shromažďovat data o přidělení paměti rozhraní .NET Framework a informace o době životnosti objektů v rozhraní .NET Framework.

 Cílovou aplikaci můžete spustit pomocí profileru; můžete připojit profiler k spuštěné instanci aplikace; a můžete vytvořit instrumentované verze aplikace pro shromažďování podrobných informací o časování spolu s daty paměti rozhraní .NET Framework.

|Úkol|Cílový typ aplikace|
|----------|-----------------------------|
|**Spuštění aplikace**|-   [Samostatné aplikace rozhraní .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**Připojení ke spuštěnému procesu**|-   [Samostatné aplikace rozhraní .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [ASP.NET webových aplikací](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Služby .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**Přístrojové moduly**|-   [Samostatné součásti rozhraní .NET Framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Staticky kompilované ASP.NET webových aplikací](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Dynamicky kompilované ASP.NET webových aplikací](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [Služby .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Použití metody souběžnosti ke shromažďování konfliktů prostředků a dat aktivity podprocesu
 Metoda souběžnosti nástrojů profilování umožňuje shromažďovat konflikty prostředků a data o aktivitách vláken a procesů z vícevláknových aplikací.

 Aplikaci můžete spustit pomocí profileru nebo můžete připojit profiler ke spuštěné instanci aplikace.

|Úkol|Cílový typ aplikace|
|----------|-----------------------------|
|**Spuštění aplikace**|-   [Samostatná aplikace rozhraní .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Samostatná nativní aplikace](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Připojení ke spuštěnému procesu**|-   [Samostatná aplikace rozhraní .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Nativní samostatná aplikace](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [ASP.NET webová aplikace](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Služba .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Nativní služba](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Přidání dat interakce vrstvy do spuštění profilování
 Přidání dat interakce vrstvy do spuštění profilování vyžaduje specifické postupy s nástroji profilování příkazového řádku. Viz [Shromažďování dat interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md)

## <a name="see-also"></a>Viz také
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
