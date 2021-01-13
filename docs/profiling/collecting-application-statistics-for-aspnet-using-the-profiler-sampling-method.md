---
title: Shromažďovat statistiky pro webové aplikace v ASP.NET
description: Projděte si postupy a možnosti pro shromažďování statistik výkonu pro webové aplikace v ASP.NET pomocí nástroje VSPerfASPNETCmd a VSPerfCmd a metody profilování vzorkování.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: ef1f4ef1c50db1234425ab164f377dab5ff12ea6
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149531"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Shromažďovat statistiky pro webové aplikace v ASP.NET

Tato část popisuje postupy a možnosti pro shromažďování statistik výkonu pro webovou aplikaci ASP.NET pomocí nástroje příkazového řádku **VSPerfASPNETCmd** a **VSPerfCmd** a metody profilování vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> I když nástroj **VSPerfCmd** poskytuje úplný přístup k funkcím nástroje pro profilaci, včetně pozastavení a obnovení profilování a shromažďování dalších dat z čítačů výkonu procesoru a systému Windows, byste měli použít nástroj příkazového řádku  **VSPerfASPNETCmd** , pokud tuto funkci nepotřebujete. Nástroj příkazového řádku **VSPerfASPNETCmd** je upřednostňovanou metodou při profilaci webů ASP.NET pomocí samostatného profileru. V porovnání s nástrojem příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) není nutné nastavit žádné proměnné prostředí a restartování počítače není vyžadováno. Další informace najdete v tématu [rychlé profilování webu pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Připojení profileru k aplikaci ASP.NET**|-   [Postupy: Připojení profileru k webové aplikaci ASP.NET ke shromažďování statistik aplikace](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-aspnet-web-applications"></a>ASP.NET webové aplikace Profile

|Úkol|Související obsah|
|----------|---------------------|
|**Profilování pomocí metody instrumentace**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Přidělení paměti profilu a uvolňování paměti**|-   [Shromáždit data paměti](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Kolize prostředku profilu a aktivita vlákna**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>Sample – metoda

|Úkol|Související obsah|
|----------|---------------------|
|**Samostatné (klientské) aplikace profilu**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **Profilovací služby**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analýza zobrazení a sestav vzorkování dat
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
