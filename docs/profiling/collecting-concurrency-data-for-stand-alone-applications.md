---
title: Příkazový řádek profileru – získání dat souběžnosti aplikace v samostatné aplikaci
description: Shromažďování dat souběžnosti pro samostatné aplikace pomocí příkazového řádku profileru v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 24cd41210628bc507b3666e57f9cdc2abf609a6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868434"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Shromažďování dat souběžnosti pro samostatné aplikace pomocí příkazového řádku profileru
Metoda souběžnosti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci umožňuje shromažďovat data o kolize prostředku a data aktivity vláken, která ukazují využití procesoru, kolize vláken, migraci vláken, zpoždění synchronizace, oblasti překrývajících se vstupně-výstupní operace a další systémové události.

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Spuštění .NET Framework aplikace a dat o souběžnosti profilů**|-   [Postupy: spuštění aplikace .NET Framework pro shromažďování dat souběžnosti](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**Spuštění aplikace C/C++ a dat o souběžnosti profilů**|-   [Postupy: spuštění nativní aplikace pro shromažďování dat souběžnosti](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Připojení profileru k běžící .NET Framework aplikaci**|-   [Postupy: Připojení profileru k aplikaci .NET Framework ke shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Připojení profileru k běžící aplikaci C/C++**|-   [Postupy: Připojení profileru k nativní aplikaci a shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-stand-alone-applications"></a>Profilovat samostatné aplikace

|Úkol|Související obsah|
|----------|---------------------|
|**Profilování pomocí metody vzorkování**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profilování pomocí metody instrumentace**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profilové přidělení paměti .NET a uvolňování paměti**|-   [Shromažďování dat .NET Framework paměti](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Přidat data interakce vrstev**|-   [Shromáždit data interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Problémy s souběžným profilací

|Úkol|Související obsah|
|----------|---------------------|
|**Profilování aplikací ASP.NET**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Profilovací služby**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analýza zobrazení a sestav souběžnosti dat
- [Zobrazení dat kolizí prostředků](../profiling/resource-contention-data-views.md)

- [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Reference
- [Referenční dokumentace nástrojů příkazového řádku pro profilaci](../profiling/command-line-profiling-tools-reference.md)
