---
title: Shromažďování statistik samostatné aplikace pomocí příkazového řádku profileru
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 589dae38917e43f9b832fb2d3475bf63546a2e31
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331885"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Shromažďování statistik aplikace pro samostatné aplikace pomocí příkazového řádku profileru
Tato část popisuje postupy a možnosti pro shromažďování statistik výkonu pro aplikaci klienta (samostatné) pomocí metody vzorkování z příkazového řádku.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Spuštění aplikace pomocí profilace**|-   [Postupy: spuštění samostatné aplikace a shromažďování statistik aplikace](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Připojení profileru k běžící .NET Framework aplikaci**|-   [Postupy: Připojení profileru k aplikaci .NET Framework a shromáždění statistik aplikace](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**Připojení profileru k běžící aplikaci C/C++**|-   [Postupy: Připojení profileru k nativní aplikaci a shromažďování statistik aplikace](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**Přidat data interakce vrstev**|-   [Shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-stand-alone-applications"></a>Profilovat samostatné aplikace

|Úkol|Související obsah|
|----------|---------------------|
|**Instrumentace aplikace**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Shromažďovat data o přidělování paměti .NET a shromažďování paměti**|-   [Shromažďování dat .NET Framework paměti](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Shromažďovat data o kolize prostředků a provádění vláken**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profilování pomocí metody vzorkování

|Úkol|Související obsah|
|----------|---------------------|
|**ASP.NET webové aplikace Profile**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profilovací služby**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). V této části najdete popis postupu shromažďování statistik výkonu ze služeb systému Windows pomocí metody vzorkování.|

### <a name="analyze-sampling-data-views-and-reports"></a>Analýza zobrazení a sestav vzorkování dat
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
