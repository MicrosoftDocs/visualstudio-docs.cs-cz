---
title: Shromažďovat statistiky aplikací pomocí metody vzorkování profileru
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 17217a51c58e1d30b6e6854ee9dbb0c1fb662a3a
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779685"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Shromažďování statistik aplikace pro služby pomocí metody vzorkování profileru
Tato část popisuje postupy a možnosti pro shromažďování statistik výkonu pro služby systému Windows pomocí metody vzorkování z příkazového řádku.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úlohy

|Úloha|Související obsah|
|----------|---------------------|
|**Připojení profileru ke službě .NET**|-   [Postupy: Připojení profileru ke službě .NET ke shromažďování statistik aplikace](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Přidat data interakce vrstev**|-   [shromažďovat data interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Připojení profileru ke službě C/C++ Service**|-   [Postupy: Připojení profileru k nativní službě ke shromažďování statistik aplikace](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-windows-services"></a>Profilace služeb systému Windows

|Úloha|Související obsah|
|----------|---------------------|
|**Profilování pomocí metody instrumentace**|-   [shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profilové přidělení paměti .NET a uvolňování paměti**|-   [shromažďovat data paměti .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Kolize prostředku profilu a aktivita vlákna**|-   [shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profilování pomocí metody vzorkování

|Úloha|Související obsah|
|----------|---------------------|
|**Samostatné (klientské) aplikace profilu**|-   [shromažďovat statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**ASP.NET webové aplikace Profile**|-   [shromažďovat statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analýza zobrazení a sestav vzorkování dat
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
