---
title: Profiler příkazového řádku – získání dat paměti webové aplikace v ASP.NET
description: Naučte se používat nástroj příkazového řádku VSPerfCmd ke shromáždění přidělení paměti a data životnosti objektu pro webovou aplikaci ASP.NET.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: b2cb0e199e543152b9d11da4b4de014c9465c1b7
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533768"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Shromažďování dat paměti z webové aplikace ASP.NET pomocí příkazového řádku profileru
Tato část popisuje postupy a možnosti pro shromažďování přidělení paměti a dat o životnosti objektů pro webovou aplikaci v ASP.NET pomocí nástroje příkazového řádku **VSPerfCmd** .

> [!NOTE]
> Nástroj **VSPerfCmd** poskytuje úplný přístup k funkcím nástroje pro profilaci, včetně pozastavení a obnovení profilování a shromažďování dalších dat z čítačů výkonu procesoru a systému Windows. Nástroj příkazového řádku  **VSPerfASPNETCmd** můžete použít také v případě, že tuto funkci nepotřebujete. V porovnání s nástrojem příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) není nutné nastavit žádné proměnné prostředí a restartování počítače není vyžadováno. Další informace najdete v tématu [rychlé profilování webu pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Připojení profileru k běžící aplikaci ASP.NET**|-   [Postupy: Připojení profileru k webové aplikaci ASP.NET ke shromažďování dat paměti](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Instrumentace staticky kompilovaných binárních souborů**|-   [Postupy: Instrumentace staticky kompilované aplikace ASP.NET a shromažďování dat paměti](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Instrumentace dynamicky kompilovaných binárních souborů**|-   [Postupy: instrumentace dynamicky kompilované aplikace ASP.NET a shromažďování dat paměti](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-aspnet-web-applications"></a>ASP.NET webové aplikace Profile

|Úkol|Související obsah|
|----------|---------------------|
|**Profilování pomocí metody vzorkování**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profilování pomocí metody instrumentace**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Kolize prostředku profilu a aktivita vlákna**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>Profilovat data .NET Framework paměti

|Úkol|Související obsah|
|----------|---------------------|
|**Samostatné (klientské) aplikace profilu**|-   [Shromažďování dat .NET Framework paměti](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Profilovací služby**|-   [Shromažďovat data paměti .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>Analýza zobrazení a sestav dat paměti .NET
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Reference
- [Referenční dokumentace nástrojů příkazového řádku pro profilaci](../profiling/command-line-profiling-tools-reference.md)
