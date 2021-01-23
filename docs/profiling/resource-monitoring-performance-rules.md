---
title: Pravidla výkonu monitorování prostředků | Microsoft Docs
description: Zjistěte, jak zprávy o výkonu v kategorii monitorování prostředků poskytují další údaje o výkonu aplikace.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 96cad46cd8a42346ab6199bca664cdc885bfc3cd
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720264"
---
# <a name="resource-monitoring-performance-rules"></a>Pravidla výkonu sledování prostředků
Zprávy o výkonu v kategorii monitorování prostředků poskytují další údaje o výkonu aplikace. Tato data můžete použít k analýze problémů s výkonem. Tato pravidla jsou informativní a nahlášené při každém spuštění profilace.

|Pravidlo|Popis|
|-|-|
|[DA0501: Průměrná spotřeba procesoru procesem profilace.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Tato zpráva oznamuje procento času, po který procesor byl zaneprázdněn prováděním pokynů z aplikace. Vykazovaná hodnota je průměr ve všech intervalech měření, v nichž byl proces profilace aktivní.|
|[DA0502: Maximální spotřeba procesoru profilovaným procesem](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Tato zpráva oznamuje maximální procento času, po který procesor zaneprázdněn prováděním pokynů z aplikace. Vykazovaná hodnota je maximální hodnota hlášená mezi všemi měřicími intervaly, ve kterých je proces profilace aktivní.|
|[DA0503: Průměrná pracovní sada v bajtech profilovaného procesu](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Tato zpráva oznamuje průměrnou velikost fyzické paměti (v bajtech), kterou proces používal, zatímco profilace byla aktivní. Tato míra fyzické paměti se označuje jako pracovní sada.|
|[DA0504: Maximální pracovní sada v bajtech profilovaného procesu](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Tato zpráva oznamuje maximální velikost fyzické paměti (v bajtech), kterou proces používal, zatímco profilace byla aktivní.|
|[DA0505: Průměrné nesdílené bajty přidělené profilovanému procesu](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Tato zpráva oznamuje průměrnou velikost virtuální paměti, kterou proces přidělený v bajtech během profilace aktivní. Tato míra virtuální paměti se označuje jako *Soukromé bajty*. Soukromé bajty představují umístění virtuální paměti, která byla přidělena procesu, ke kterému lze přistupovat pouze v vláknech spuštěných uvnitř procesu.|
|[DA0506: Maximální nesdílené bajty přidělené profilovanému procesu](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Tato zpráva oznamuje maximální velikost virtuální paměti, kterou proces přidělený během profilace je v privátních bajtech.|
