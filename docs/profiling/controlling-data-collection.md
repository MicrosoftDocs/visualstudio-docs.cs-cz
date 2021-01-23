---
title: Řízení shromažďování dat | Microsoft Docs
description: Naučte se spouštět a zastavovat Nástroje pro profilaci shromažďování dat a jak omezit objekty, pro které se shromažďují data profilace. Tento článek je přehled.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b846db263c95f20c6ea4cb6a418973830a5dd8ee
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720927"
---
# <a name="control-data-collection"></a>Řízení shromažďování dat
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci vám umožní řídit, kdy se data profilace shromažďují během relace výkonu, a určit funkce, které jsou profilované. Tato část popisuje, jak spustit a zastavit shromažďování dat z oken **prohlížeč výkonu** a **kolekce dat** a jak omezit objekty, pro které se shromažďují data profilace.

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Spustit a zastavit profilaci:** Můžete začít profilovat aplikaci při spuštění aplikace nebo můžete připojit profiler k procesu, který je již spuštěn. Pokud je cílová aplikace spuštěna, je shromažďování dat možné pozastavit a obnovit. Ukončení relace profilování lze provést ukončením cílové aplikace nebo odpojením profileru od spuštěného procesu.|-   [Postupy: spuštění a ukončení shromažďování dat výkonu](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Postupy: připojení a odpojení nástrojů výkonu ke spouštění procesů](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Postupy: pozastavení a obnovení shromažďování údajů o výkonu](../profiling/how-to-pause-and-resume-performance-data-collection.md)|
|**Konfigurace profilace instrumentace pro omezení shromážděných dat:** Pomocí vlastností konfigurace relace výkonu můžete omezit data shromažďovaná v rámci profilace, která používají metodu instrumentace. Je možné zahrnout nebo vyloučit určité knihovny dll, obory názvů, třídy a funkce. Je také možné vyloučit funkce, které nesplňují zadanou mezní hodnotu velikosti.|-   [Postupy: omezení instrumentace na konkrétní knihovny DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Postupy: omezení instrumentace na konkrétní funkce](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Postupy: vyloučení nebo zahrnutí krátkých funkcí z instrumentace](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|

## <a name="related-sections"></a>Související oddíly
- [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)

## <a name="see-also"></a>Viz také
- [Prohlížeč výkonu](../profiling/performance-explorer.md)
