---
title: Souhrnné zobrazení – data paměti .NET | Microsoft Docs
description: Přečtěte si, jak souhrnné zobrazení zobrazuje informace o funkcích a typech .NET, které přidělují nejvíc paměti.
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
ms.openlocfilehash: 590705e7fb55315176d5533a9cd009784430ea4d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722669"
---
# <a name="summary-view---net-memory-data"></a>Souhrnné zobrazení – data paměti .NET
V souhrnném zobrazení se zobrazí informace o funkcích a typech .NET, které přidělují nejvíc paměti, a typy, které byly vytvořeny ve většině případů při spuštění profilace. Další informace, včetně popisu odkazů na oznámení a seznamů sestav, najdete v tématu [souhrnné zobrazení](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Graf časové osy
 Graf časové osy v zobrazení Souhrn ukazuje využití procesoru profilované aplikací v době, kdy k profilaci došlo. Graf časové osy můžete použít k filtrování zobrazení do vybraného časového rozsahu. Další informace najdete v tématu [Postup: filtrování zobrazení sestav na časové ose souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="functions-allocating-most-memory"></a>Funkce, které přiděluje většinu paměti
 Zobrazuje seznam funkcí, které přidělily největší počet bajtů paměti při spuštění profilace.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název funkce|
|**Psaný**|Procento všech přidělených bajtů v běhu profilace, které byly přiděleny touto funkcí nebo podřízenou funkcí volanou touto funkcí.|

## <a name="types-with-most-memory-allocated"></a>Typy s největším množstvím přidělené paměti
 Zobrazí seznam typů, pro které byl při spuštění profilování přidělen největší počet bajtů paměti.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název typu|
|**Psaný**|Procento všech přidělených bajtů v běhu profilace, které byly přiděleny pro tento typ.|

## <a name="types-with-most-instances"></a>Typy s největší instancí
 Zobrazí seznam typů, které byly vytvořeny ve většině případů během spuštění profilace. hlíží

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název typu|
|**Instance**|Procentuální podíl celkového počtu objektů of.NET vytvořených při spuštění profilace, které byly instancemi tohoto typu.|

## <a name="see-also"></a>Viz také
- [Souhrnné zobrazení – vzorkování dat](../profiling/summary-view-sampling-data.md)
- [Souhrnné zobrazení – data instrumentace](../profiling/summary-view-instrumentation-data.md)
