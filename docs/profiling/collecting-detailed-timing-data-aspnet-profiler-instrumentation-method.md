---
title: 'VSPerfCmd: Získejte časovací data pro ASP.NET webovou aplikaci pomocí instrumentace'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779646"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Shromažďování podrobných časovacích dat pro ASP.NET webovou aplikaci pomocí metody instrumentace profileru z příkazového řádku
Tato část popisuje postupy a možnosti pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] shromažďování podrobných dat o výkonu pro webovou aplikaci pomocí nástroje příkazového řádku **VSPerfCmd** a metody instrumentace.

> [!NOTE]
> Nástroj **VSPerfCmd** poskytuje úplný přístup k funkcím nástrojů profilování, včetně pozastavení a obnovení profilování a shromažďování dalších dat z čítačů výkonu procesoru a systému Windows. Nástroj příkazového řádku **VSPerfASPNETCmd** můžete také použít, pokud tuto funkci nepotřebujete. Ve srovnání s nástrojem příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) není nutné nastavit žádné proměnné prostředí a restartování počítače není vyžadováno. Další informace naleznete v tématu [Rapid web profilování s VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Profil staticky zkompilované binární soubory**|-   [Postup: Nástroj staticky sestavené ASP.NET aplikace a shromažďování podrobných časových dat](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Profil dynamicky kompilované binární soubory**|-   [Postup: Instrumentujte dynamicky sestavenou ASP.NET aplikaci a shromažďujte podrobné časovací údaje](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>Související úlohy

### <a name="profile-aspnet-web-applications"></a>Profil ASP.NET webových aplikací

|Úkol|Související obsah|
|----------|---------------------|
|**Profil pomocí metody odběru vzorků**|-   [Shromažďujte statistiky aplikací pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Přidělení a uvolnění paměti profilu**|-   [Shromažďování paměťových dat](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Konflikty prostředků profilu a aktivita podprocesu**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>Profil pomocí metody instrumentace

|Úkol|Související obsah|
|----------|---------------------|
|**Profilovat samostatné (klientské) aplikace**|-   [Shromažďování podrobných časových dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profilové služby**|-   [Shromažďování podrobných časových dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>Analýza zobrazení a sestav dat instrumentace
- [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)
