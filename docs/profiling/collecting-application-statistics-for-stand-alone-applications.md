---
title: Použití příkazového řádku profileru ke shromažďování statistik samostatných aplikací
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: de399bf493e328e583bdd2765822ca3a66144698
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779633"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Shromažďování statistik aplikace pro samostatné aplikace pomocí příkazového řádku profileru
Tato část popisuje postupy a možnosti pro shromažďování statistik výkonu pro klientskou (samostatnou) aplikaci pomocí metody vzorkování z příkazového řádku.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Spuštění aplikace pomocí profilování**|-   [Postup: Spuštění samostatné aplikace a shromažďování statistik aplikací](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Připojení profileru ke spuštěné aplikaci rozhraní .NET Framework**|-   [Postup: Připojení profileru k aplikaci rozhraní .NET Framework a shromažďování statistik aplikací](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**Připojení profileru ke spuštěné aplikaci C/C++**|-   [Postup: Připojení profileru k nativní aplikaci a shromažďování statistik aplikací](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**Přidání dat interakce na úrovni**|-   [Shromažďování dat interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-stand-alone-applications"></a>Profilovat samostatné aplikace

|Úkol|Související obsah|
|----------|---------------------|
|**Nástroj aplikace**|-   [Shromažďování podrobných časových dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Shromažďovat data o přidělení paměti .NET a uvolňování paměti**|-   [Shromažďování paměťových dat rozhraní .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Shromažďování tvrzení o prostředcích a dat provádění vláken**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profil pomocí metody odběru vzorků

|Úkol|Související obsah|
|----------|---------------------|
|**Profil ASP.NET webových aplikací**|-   [Shromažďujte statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profilové služby**|-   [Shromažďujte statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Popisuje, jak shromažďovat statistiky výkonu ze služeb systému Windows pomocí metody vzorkování.|

### <a name="analyze-sampling-data-views-and-reports"></a>Analýza zobrazení a sestav vzorkovacích dat
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
