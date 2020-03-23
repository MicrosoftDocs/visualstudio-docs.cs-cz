---
title: Souhrnné zobrazení - Data instrumentace | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2f52f80cad4ce7678a832a7b76a75d8f2fd4460e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778216"
---
# <a name="summary-view---instrumentation-data"></a>Souhrnné zobrazení – data instrumentace
Souhrnné zobrazení zobrazuje informace o nejvíce výkon-nákladné funkce v profilování spustit. Další informace, včetně popisu odkazů na oznámení a seznamů sestav, naleznete v [tématu Souhrnné zobrazení](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Graf časové osy
 Graf časové osy v souhrnném zobrazení zobrazuje využití procesoru (CPU) profilovanou aplikací v době, kdy došlo k profilování. Graf časové osy můžete použít k filtrování zobrazení na vybrané časové rozpětí. Další informace naleznete v [tématu Postup: Filtrování zobrazení sestavy z časové osy souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="hot-path"></a>Horká cesta
 **Horká cesta** zobrazuje cestu spuštění, která spotřebovává nejvíce času. Klepnutím na funkci zobrazíte zobrazení Podrobnosti funkce pro funkci. Chcete-li zobrazit další zobrazení funkce, klepněte pravým tlačítkem myši na funkci a potom klepněte na zobrazení ze seznamu.

 **Horká cesta** obsahuje následující data pro každou funkci:

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název funkce.|
|**Uplynulý včetně času %**|Procento všech čas v profilování dat, které funkce strávil provádění kódu v jeho tělo funkce a ve funkcích, které volá.|
|**Uplynulý výhradní čas %**|Procento všech čas v profilování dat, které funkce strávil provádění kódu v jeho těle funkce. Čas strávený ve funkcích, které funkce volá není zahrnuta.|

## <a name="functions-with-most-individual-work"></a>Funkce s většinou individuální práce
 Seznam funkcí, které spotřebovávaly nejvíce času provádění kódu v těle funkce a nikoli ve funkcích, které volal.

 **Funkce s většinou individuální práce** obsahuje následující data pro každou funkci:

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název funkce.|
|**Exkluzivní čas %**|Procento všech čas v profilování dat, které funkce strávil provádění kódu v jeho těle funkce. Čas strávený ve funkcích, které funkce volá není zahrnuta.|

## <a name="see-also"></a>Viz také
- [Souhrnné zobrazení – vzorkovací data](../profiling/summary-view-sampling-data.md)
- [Souhrnné zobrazení - data paměti .NET](../profiling/summary-view-dotnet-memory-data.md)
