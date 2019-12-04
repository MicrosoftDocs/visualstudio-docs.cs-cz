---
title: Příkazový řádek profileru pro získání dat souběžnosti aplikace v samostatné aplikaci
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6180d2f2e3ed655f378900d3d41691daa98a0354
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74773254"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Shromažďování dat souběžnosti pro samostatné aplikace pomocí příkazového řádku profileru
Metoda souběžnosti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci umožňuje shromažďovat data o kolize prostředků a data aktivity vláken, která vám ukazují využití procesoru, kolize vláken, migraci vláken, zpoždění synchronizace, oblasti překrývajících se vstupně-výstupní operace a další systémové události.

## <a name="common-tasks"></a>Běžné úlohy

|Úloha|Související obsah|
|----------|---------------------|
|**Spuštění .NET Framework aplikace a dat o souběžnosti profilů**|-   [Postupy: spuštění aplikace .NET Framework ke shromáždění dat souběžnosti](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**Spuštění dat souběžnostiC++ v C/a aplikace a profilu**|-   [Postupy: spuštění nativní aplikace pro shromažďování dat souběžnosti](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Připojení profileru k běžící .NET Framework aplikaci**|-   [Postupy: Připojení profileru k aplikaci .NET Framework ke shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Připojení profileru k běžícímu C/C++ aplikaci**|-   [Postupy: Připojení profileru k nativní aplikaci a shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-stand-alone-applications"></a>Profilovat samostatné aplikace

|Úloha|Související obsah|
|----------|---------------------|
|**Profilování pomocí metody vzorkování**|-   [shromažďovat statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profilování pomocí metody instrumentace**|-   [shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profilové přidělení paměti .NET a uvolňování paměti**|-   [shromažďovat data o .NET Framework paměti](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Přidat data interakce vrstev**|-   [shromažďovat data interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Problémy s souběžným profilací

|Úloha|Související obsah|
|----------|---------------------|
|**Profilování aplikací ASP.NET**|-   [shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Profilovací služby**|-   [shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analýza zobrazení a sestav souběžnosti dat
- [Zobrazení dat kolizí prostředků](../profiling/resource-contention-data-views.md)

- [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Odkaz
- [Referenční dokumentace nástrojů příkazového řádku pro profilaci](../profiling/command-line-profiling-tools-reference.md)
