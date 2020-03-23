---
title: Pravidla výkonnosti monitorování zdrojů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2389c23b9089ebbdd96d337a3b47d5be9d576b4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778320"
---
# <a name="resource-monitoring-performance-rules"></a>Pravidla výkonu sledování prostředků
Zprávy o výkonu v kategorii Monitorování prostředků poskytují další data o výkonu aplikace. Tato data můžete použít k analýze problémů s výkonem. Tato pravidla jsou informační a jsou hlášena pro každé profilování.

|||
|-|-|
|[DA0501: Průměrná spotřeba procesoru procesem, který je profilován.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Tato zpráva hlásí procento času, po který byl procesor zaneprázdněn prováděním pokynů z aplikace. Vykázaná hodnota je průměr za všechny intervaly měření, ve kterých byl profilovaný proces aktivní.|
|[DA0502: Maximum spotřeby procesoru profilovaným procesem](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Tato zpráva hlásí maximální procento času, po které byl procesor zaneprázdněn prováděním pokynů z aplikace. Vykázaná hodnota je maximální hodnota vykázaná mezi všemi intervaly měření, ve kterých byl profilovaný proces aktivní.|
|[DA0503: Průměr Pracovní sady v bajtech pro profilovaný Proces](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Tato zpráva hlásí průměrné množství fyzické paměti v bajtů, které proces používal, zatímco profilování bylo aktivní. Tato míra fyzické paměti se označuje jako pracovní sada.|
|[DA0504: Maximum pracovní sady v bajtech pro profilovaný proces](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Tato zpráva hlásí maximální množství fyzické paměti v bajtů, které proces používal, zatímco profilování bylo aktivní.|
|[DA0505: Průměr Nesdílených bajtů přidělených pro profilovaný Proces](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Tato zpráva hlásí průměrné množství virtuální paměti, které proces přidělené v bajtů, zatímco profilování bylo aktivní. Tato míra virtuální paměti se označuje jako *soukromé bajty*. Soukromé bajty představují umístění virtuální paměti, které byly přiděleny procesem, ke kterému lze přistupovat pouze podprocesy spuštěné uvnitř procesu.|
|[DA0506: Maximum Nesdílených bajtů přidělených pro profilovaný Proces](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Tato zpráva hlásí maximální množství virtuální paměti, které proces přidělené v soukromých bajtů, zatímco profilování bylo aktivní.|
