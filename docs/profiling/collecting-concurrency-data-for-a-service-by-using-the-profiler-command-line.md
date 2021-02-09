---
title: Příkazový řádek profileru – získání dat souběžnosti pro službu
description: Shromažďovat data o kolize prostředků a data aktivity vláken pomocí metody souběžnosti sady Visual Studio Nástroje pro profilaci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8ae2d3678ec05ce583c9c0b7daf202f3272f4b77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868449"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Shromažďování dat souběžnosti pro službu pomocí příkazového řádku profileru
Metoda souběžnosti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci umožňuje shromažďovat data o kolize prostředku a data aktivity vláken, která ukazují využití procesoru, kolize vláken, migraci vláken, zpoždění synchronizace, oblasti překrývajících se vstupně-výstupní operace a další systémové události.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Připojit ke spuštěné službě .NET**|-   [Postupy: Připojení profileru ke službě .NET ke shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Přidat data interakce vrstev**|-   [Shromáždit data interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Připojit ke spuštěné službě C/C++**|-   [Postupy: Připojení profileru k nativní službě ke shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-windows-services"></a>Profilace služeb systému Windows

|Úkol|Související obsah|
|----------|---------------------|
|**Profilování pomocí metody vzorkování**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Profilování pomocí metody instrumentace**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Přidělení a uvolňování paměti Profile.NET**|-   [Shromažďovat data paměti .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Data souběžnosti profilů

|Úkol|Související obsah|
|----------|---------------------|
|**Profilovat samostatné aplikace**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**ASP.NET webové aplikace Profile**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analýza zobrazení a sestav souběžnosti dat
- [Zobrazení dat kolizí prostředků](../profiling/resource-contention-data-views.md)

- [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Reference
- [Referenční dokumentace nástrojů příkazového řádku pro profilaci](../profiling/command-line-profiling-tools-reference.md)
