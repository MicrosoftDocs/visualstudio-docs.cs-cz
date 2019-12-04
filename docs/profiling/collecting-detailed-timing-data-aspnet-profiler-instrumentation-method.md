---
title: 'VSPerfCmd: Získejte data časování pro webovou aplikaci ASP.NET pomocí instrumentace.'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: d764ef32cdcb061992817d433dabb6ae61b64fd9
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779646"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Shromažďování podrobných dat časování pro webovou aplikaci v ASP.NET pomocí metody instrumentace profileru z příkazového řádku
Tato část popisuje postupy a možnosti pro shromažďování podrobných údajů o výkonu pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace pomocí nástroje příkazového řádku **VSPerfCmd** a metody instrumentace.

> [!NOTE]
> Nástroj **VSPerfCmd** poskytuje úplný přístup k funkcím nástroje pro profilaci, včetně pozastavení a obnovení profilování a shromažďování dalších dat z čítačů výkonu procesoru a systému Windows. Nástroj příkazového řádku **VSPerfASPNETCmd** můžete použít také v případě, že tuto funkci nepotřebujete. V porovnání s nástrojem příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) není nutné nastavit žádné proměnné prostředí a restartování počítače není vyžadováno. Další informace najdete v tématu [rychlé profilování webu pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Běžné úlohy

|Úloha|Související obsah|
|----------|---------------------|
|**Profil staticky kompilovaných binárních souborů**|-   [Postupy: Instrumentace staticky kompilované aplikace ASP.NET a shromažďování podrobných dat časování](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Profilování dynamicky kompilovaných binárních souborů**|-   [Postupy: instrumentace dynamicky kompilované aplikace ASP.NET a shromažďování podrobných dat časování](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-aspnet-web-applications"></a>ASP.NET webové aplikace Profile

|Úloha|Související obsah|
|----------|---------------------|
|**Profilování pomocí metody vzorkování**|-   [shromažďovat statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Přidělení paměti profilu a uvolňování paměti**|-   [shromažďovat data paměti](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Kolize prostředku profilu a aktivita vlákna**|-   [shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>Profilování pomocí metody instrumentace

|Úloha|Související obsah|
|----------|---------------------|
|**Samostatné (klientské) aplikace profilu**|-   [shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profilovací služby**|-   [shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>Analýza zobrazení a sestav dat instrumentace
- [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)
