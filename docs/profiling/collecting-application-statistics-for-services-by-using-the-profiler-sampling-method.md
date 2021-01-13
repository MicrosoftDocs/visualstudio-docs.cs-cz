---
title: Shromáždit statistiky pro služby systému Windows – Metoda vzorkování profileru
description: Projděte si postupy a možnosti pro shromažďování statistik výkonu pro služby systému Windows pomocí metody vzorkování profilace z příkazového řádku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f4c686de4128d655b5b8146925529e6a280bb754
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148335"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Shromažďování statistik aplikace pro služby pomocí metody vzorkování profileru
Tato část popisuje postupy a možnosti pro shromažďování statistik výkonu pro služby systému Windows pomocí metody vzorkování z příkazového řádku.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Připojení profileru ke službě .NET**|-   [Postupy: Připojení profileru ke službě .NET ke shromažďování statistik aplikace](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Přidat data interakce vrstev**|-   [Shromáždit data interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Připojení profileru ke službě C/C++**|-   [Postupy: Připojení profileru k nativní službě ke shromažďování statistik aplikace](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-windows-services"></a>Profilace služeb systému Windows

|Úkol|Související obsah|
|----------|---------------------|
|**Profilování pomocí metody instrumentace**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profilové přidělení paměti .NET a uvolňování paměti**|-   [Shromažďovat data paměti .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Kolize prostředku profilu a aktivita vlákna**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profilování pomocí metody vzorkování

|Úkol|Související obsah|
|----------|---------------------|
|**Samostatné (klientské) aplikace profilu**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**ASP.NET webové aplikace Profile**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analýza zobrazení a sestav vzorkování dat
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
