---
title: Souhrnné zobrazení – data paměti .NET | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: a67902af99eaee6c75f92f86c2481dfc2afd744e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771553"
---
# <a name="summary-view---net-memory-data"></a>Souhrnné zobrazení - data paměti .NET
Souhrnné zobrazení zobrazuje informace o funkcích a typech rozhraní .NET, které přidělili nejvíce paměti, a o typech, které byly vytvořeny nejčastěji při profilování. Další informace, včetně popisu odkazů na oznámení a seznamů sestav, naleznete v [tématu Souhrnné zobrazení](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Graf časové osy
 Graf časové osy v souhrnném zobrazení zobrazuje využití procesoru (CPU) profilovanou aplikací v době, kdy došlo k profilování. Graf časové osy můžete použít k filtrování zobrazení na vybrané časové rozpětí. Další informace naleznete v [tématu Postup: Filtrování zobrazení sestavy z časové osy souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="functions-allocating-most-memory"></a>Funkce přidělování většiny paměti
 Uvádí funkce, které přidělili největší počet bajtů paměti v profilování spustit.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název funkce.|
|**Bajty %**|Procento všech přidělených bajtů v profilování spustit, které byly přiděleny touto funkcí nebo podřízené funkce, která byla volána touto funkcí.|

## <a name="types-with-most-memory-allocated"></a>Typy s nejvíce přidělené paměti
 Seznam typů, pro které byl při profilování přidělen největší počet bajtů paměti.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název typu|
|**Bajty %**|Procento všech přidělených bajtů v profilování spustit, které byly přiděleny pro tento typ.|

## <a name="types-with-most-instances"></a>Typy s většinou instancí
 Uvádí typy, které byly vytvořeny nejvíce krát během profilování spustit. Hda

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název typu|
|**Instance %**|Procento z celkového počtu of.NET objekty, které byly vytvořeny v profilování spustit, které byly instance tohoto typu.|

## <a name="see-also"></a>Viz také
- [Souhrnné zobrazení – vzorkovací data](../profiling/summary-view-sampling-data.md)
- [Souhrnné zobrazení – data instrumentace](../profiling/summary-view-instrumentation-data.md)
