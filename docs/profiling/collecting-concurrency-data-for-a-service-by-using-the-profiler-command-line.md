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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779672"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Shromažďování dat souběžnosti pro službu pomocí příkazového řádku profileru
Metoda souběžnosti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástrojů profilování umožňuje shromažďovat data o konfliktu prostředků a data o aktivitě vláken, která zobrazuje využití procesoru, konflikty vláken, migraci vláken, zpoždění synchronizace, oblasti překrývajících se vi a další systémové události.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Připojení ke spuštěné službě .NET**|-   [Postup: Připojení profileru ke službě .NET ke shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Přidání dat interakce na úrovni**|-   [Shromažďování dat interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Připojení ke spuštěné službě C/C++**|-   [Postup: Připojení profileru k nativní službě ke shromažďování dat souběžnosti](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-windows-services"></a>Profil služby systému Windows

|Úkol|Související obsah|
|----------|---------------------|
|**Profil pomocí metody odběru vzorků**|-   [Shromažďujte statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Profil pomocí metody instrumentace**|-   [Shromažďování podrobných časových dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profile.NET přidělení paměti a uvolnění paměti**|-   [Shromažďování dat paměti .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Data souběžnosti profilu

|Úkol|Související obsah|
|----------|---------------------|
|**Profilovat samostatné aplikace**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**ProfilASP.NET webové aplikace**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analýza zobrazení a sestav dat souběžnosti
- [Zobrazení dat konfliktů prostředků](../profiling/resource-contention-data-views.md)

- [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Referenční informace
- [Referenční dokumentace nástrojů příkazového řádku pro profilaci](../profiling/command-line-profiling-tools-reference.md)
