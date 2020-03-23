---
title: Získání ASP.NET dat paměti webové aplikace pomocí příkazového řádku profileru
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 9e8d9fde00a2390793ae8efe05b684e73caca321
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773056"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Shromažďování paměťových dat z webové aplikace ASP.NET pomocí příkazového řádku profileru
Tato část popisuje postupy a možnosti pro shromažďování přidělení paměti a data životnosti objektu pro ASP.NET webovou aplikaci pomocí nástroje příkazového řádku **VSPerfCmd.**

> [!NOTE]
> Nástroj **VSPerfCmd** poskytuje úplný přístup k funkcím nástrojů profilování, včetně pozastavení a obnovení profilování a shromažďování dalších dat z čítačů výkonu procesoru a systému Windows. Nástroj příkazového řádku **VSPerfASPNETCmd** můžete také použít, pokud tuto funkci nepotřebujete. Ve srovnání s nástrojem příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) není nutné nastavit žádné proměnné prostředí a restartování počítače není vyžadováno. Další informace naleznete v tématu [Rapid web profilování s VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Připojení profileru ke spuštěné ASP.NET aplikaci**|-   [Postup: Připojení profileru k webové aplikaci ASP.NET shromažďovat data o paměti](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Nástroj staticky sestavené binární soubory**|-   [Postup: Nástroj staticky kompilované ASP.NET aplikace a shromažďování paměťových dat](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Nástroj dynamicky kompilované binární soubory**|-   [Postup: Instrumentujte dynamicky kompilované ASP.NET aplikace a shromažďujte paměťová data](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-aspnet-web-applications"></a>Profil ASP.NET webových aplikací

|Úkol|Související obsah|
|----------|---------------------|
|**Profil pomocí metody odběru vzorků**|-   [Shromažďujte statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profil pomocí metody instrumentace**|-   [Shromažďování podrobných časových dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Konflikty prostředků profilu a aktivita podprocesu**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>Data paměti rozhraní Profile .NET Framework

|Úkol|Související obsah|
|----------|---------------------|
|**Profilovat samostatné (klientské) aplikace**|-   [Shromažďování paměťových dat rozhraní .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Profilové služby**|-   [Shromažďování dat paměti .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>Analýza zobrazení a sestav paměti .NET
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Referenční informace
- [Referenční dokumentace nástrojů příkazového řádku pro profilaci](../profiling/command-line-profiling-tools-reference.md)
