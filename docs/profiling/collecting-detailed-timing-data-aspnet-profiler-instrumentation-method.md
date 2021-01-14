---
title: Shromažďování dat časování pro ASP.NET pomocí instrumentace
description: Naučte se používat VSPerfCmd ke shromažďování podrobných údajů o výkonu pro webovou aplikaci ASP.NET. Poskytuje úplný přístup k funkcím Nástroje pro profilaci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 1001e10d80b39df5072a6524f445c97418aa603b
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205746"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Shromažďování podrobných dat časování pro webovou aplikaci v ASP.NET pomocí metody instrumentace profileru z příkazového řádku
Tato část popisuje postupy a možnosti pro shromažďování podrobných údajů o výkonu pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci pomocí nástroje příkazového řádku **VSPerfCmd** a metody instrumentace.

> [!NOTE]
> Nástroj **VSPerfCmd** poskytuje úplný přístup k funkcím nástroje pro profilaci, včetně pozastavení a obnovení profilování a shromažďování dalších dat z čítačů výkonu procesoru a systému Windows. Nástroj příkazového řádku  **VSPerfASPNETCmd** můžete použít také v případě, že tuto funkci nepotřebujete. V porovnání s nástrojem příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) není nutné nastavit žádné proměnné prostředí a restartování počítače není vyžadováno. Další informace najdete v tématu [rychlé profilování webu pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Profil staticky kompilovaných binárních souborů**|-   [Postupy: Instrumentace staticky kompilované aplikace ASP.NET a shromažďování podrobných dat časování](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Profilování dynamicky kompilovaných binárních souborů**|-   [Postupy: instrumentace dynamicky kompilované aplikace ASP.NET a shromažďování podrobných dat časování](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-aspnet-web-applications"></a>ASP.NET webové aplikace Profile

|Úkol|Související obsah|
|----------|---------------------|
|**Profilování pomocí metody vzorkování**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Přidělení paměti profilu a uvolňování paměti**|-   [Shromáždit data paměti](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Kolize prostředku profilu a aktivita vlákna**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>Profilování pomocí metody instrumentace

|Úkol|Související obsah|
|----------|---------------------|
|**Samostatné (klientské) aplikace profilu**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profilovací služby**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>Analýza zobrazení a sestav dat instrumentace
- [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)
