---
title: Příkazový řádek Profiler pro získání samostatných dat souběžnosti aplikace
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773254"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Shromažďování dat souběžnosti pro samostatné aplikace pomocí příkazového řádku profileru
Metoda souběžnosti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástrojů profilování umožňuje shromažďovat data o konfliktu prostředků a data o aktivitě vláken, která zobrazuje využití procesoru, konflikty vláken, migraci vláken, zpoždění synchronizace, oblasti překrývajících se vi a další systémové události.

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Spuštění dat souběžnosti aplikace rozhraní .NET Framework a souběžnosti profilu**|-   [Postup: Spuštění aplikace rozhraní .NET Framework pro shromažďování dat souběžnosti](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**Spuštění dat souběžnosti aplikace c/c++ a profilu**|-   [Postup: Spuštění nativní aplikace pro shromažďování dat souběžnosti](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Připojení profileru ke spuštěné aplikaci rozhraní .NET Framework**|-   [Postup: Připojení profileru k aplikaci rozhraní .NET Framework ke shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Připojení profileru ke spuštěné aplikaci C/C++**|-   [Postup: Připojení profileru k nativní aplikaci a shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-stand-alone-applications"></a>Profilovat samostatné aplikace

|Úkol|Související obsah|
|----------|---------------------|
|**Profil pomocí metody odběru vzorků**|-   [Shromažďujte statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profil pomocí metody instrumentace**|-   [Shromažďování podrobných časových dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Přidělení a uvolnění paměti profil .NET**|-   [Shromažďování paměťových dat rozhraní .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Přidání dat interakce na úrovni**|-   [Shromažďování dat interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Problémy souběžnosti profilu

|Úkol|Související obsah|
|----------|---------------------|
|**Profilové aplikace ASP.NET**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Profilové služby**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analýza zobrazení a sestav dat souběžnosti
- [Zobrazení dat konfliktů prostředků](../profiling/resource-contention-data-views.md)

- [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Referenční informace
- [Referenční dokumentace nástrojů příkazového řádku pro profilaci](../profiling/command-line-profiling-tools-reference.md)
