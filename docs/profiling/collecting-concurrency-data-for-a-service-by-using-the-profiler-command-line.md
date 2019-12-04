---
title: Použití příkazového řádku profileru k získání dat souběžnosti pro službu
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4b7b60ad871f40e06e2a8fbf6782773ce6596f31
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779672"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Shromažďování dat souběžnosti pro službu pomocí příkazového řádku profileru
Metoda souběžnosti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci umožňuje shromažďovat data o kolize prostředků a data aktivity vláken, která vám ukazují využití procesoru, kolize vláken, migraci vláken, zpoždění synchronizace, oblasti překrývajících se vstupně-výstupní operace a další systémové události.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úlohy

|Úloha|Související obsah|
|----------|---------------------|
|**Připojit ke spuštěné službě .NET**|-   [Postupy: Připojení profileru ke službě .NET ke shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Přidat data interakce vrstev**|-   [shromažďovat data interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Připojit ke spuštěnému C/C++ službě**|-   [Postupy: Připojení profileru k nativní službě ke shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-windows-services"></a>Profilace služeb systému Windows

|Úloha|Související obsah|
|----------|---------------------|
|**Profilování pomocí metody vzorkování**|-   [shromažďovat statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Profilování pomocí metody instrumentace**|-   [shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Přidělení a uvolňování paměti Profile.NET**|-   [shromažďovat data paměti .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Data souběžnosti profilů

|Úloha|Související obsah|
|----------|---------------------|
|**Profilovat samostatné aplikace**|-   [shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**ASP.NET webové aplikace Profile**|-   [shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analýza zobrazení a sestav souběžnosti dat
- [Zobrazení dat kolizí prostředků](../profiling/resource-contention-data-views.md)

- [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Odkaz
- [Referenční dokumentace nástrojů příkazového řádku pro profilaci](../profiling/command-line-profiling-tools-reference.md)
