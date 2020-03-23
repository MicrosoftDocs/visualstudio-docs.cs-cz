---
title: Kontrolní shromažďování údajů | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 48c7047bdd321943074221c9f09193970d42a247
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777800"
---
# <a name="control-data-collection"></a>Řízení shromažďování dat
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Nástroje profilování umožňují řídit při shromažďování dat profilování během relace výkonu a určit funkce, které jsou profilovány. Tato část popisuje, jak spustit a zastavit shromažďování dat z okna **Průzkumník a** **řízení shromažďování dat** a jak omezit objekty, pro které jsou shromažďována data profilování.

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Související obsah|
|----------|---------------------|
|**Spuštění a ukončení profilování:** Můžete začít profilovat aplikaci při spuštění aplikace nebo můžete připojit profiler k procesu, který je již spuštěn. Pokud je cílová aplikace spuštěna, je shromažďování dat možné pozastavit a obnovit. Ukončení relace profilování lze provést ukončením cílové aplikace nebo odpojením profileru od spuštěného procesu.|-   [Postup: Shromažďování dat o výkonu zahájení a ukončení](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Postup: Připojení a odpojení nástrojů pro sledování spuštěných procesů](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Postup: Pozastavení a obnovení shromažďování dat o výkonu](../profiling/how-to-pause-and-resume-performance-data-collection.md)|
|**Konfigurace profilování instrumentace k omezení shromážděných dat:** Pomocí vlastností konfigurace relace výkonu můžete omezit data shromážděná v profilování spuštění, které používají metodu instrumentace. Je možné zahrnout nebo vyloučit určité knihovny dll, obory názvů, třídy a funkce. Je také možné vyloučit funkce, které nesplňují zadanou mezní hodnotu velikosti.|-   [Postup: Omezení instrumentace na konkrétní knihovny DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Postup: Omezení instrumentace na konkrétní funkce](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Postup: Vyloučení nebo zahrnutí krátkých funkcí z instrumentace](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|

## <a name="related-sections"></a>Související oddíly
- [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)

## <a name="see-also"></a>Viz také
- [Prohlížeč výkonu](../profiling/performance-explorer.md)
