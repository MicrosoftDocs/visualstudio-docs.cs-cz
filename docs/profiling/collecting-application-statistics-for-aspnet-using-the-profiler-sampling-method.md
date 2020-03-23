---
title: Shromažďovat statistiky pro webové aplikace ASP.NET | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: a2cae807a8d833cf2653ea23616eeb819673229e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773241"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Shromažďování statistik pro ASP.NET webových aplikací

Tato část popisuje postupy a možnosti pro shromažďování statistik výkonu pro ASP.NET webové aplikace pomocí nástroje příkazového řádku **VSPerfASPNETCmd** a **VSPerfCmd** a metody profilování vzorkování.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Přestože nástroj **VSPerfCmd** poskytuje úplný přístup k funkcím nástroje profilování, včetně pozastavení a obnovení profilování a shromažďování dalších dat z čítačů výkonu procesoru a systému Windows, měli byste použít nástroj příkazového řádku **VSPerfASPNETCmd,** pokud tuto funkci nepotřebujete. Nástroj příkazového řádku **VSPerfASPNETCmd** je upřednostňovanou metodou při profilování ASP.NET webových serverech pomocí samostatného profileru. Ve srovnání s nástrojem příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) není nutné nastavit žádné proměnné prostředí a restartování počítače není vyžadováno. Další informace naleznete v tématu [Rapid web profilování s VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Připojení profileru k ASP.NET aplikaci**|-   [Postup: Připojení profileru k ASP.NET webové aplikaci ke shromažďování statistik aplikací](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-aspnet-web-applications"></a>Profil ASP.NET webových aplikací

|Úkol|Související obsah|
|----------|---------------------|
|**Profil pomocí metody instrumentace**|-   [Shromažďování podrobných časových dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Přidělení a uvolnění paměti profilu**|-   [Shromažďování paměťových dat](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Konflikty prostředků profilu a aktivita podprocesu**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>Vzorová metoda

|Úkol|Související obsah|
|----------|---------------------|
|**Profilovat samostatné (klientské) aplikace**|-   [Shromažďujte statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **Profilové služby**|-   [Shromažďujte statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analýza zobrazení a sestav vzorkovacích dat
- [Zobrazení dat metody vzorkování](../profiling/profiler-sampling-method-data-views.md)
