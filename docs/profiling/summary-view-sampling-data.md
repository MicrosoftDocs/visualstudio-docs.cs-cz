---
title: Souhrnné zobrazení – vzorkovací data | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 649d0e9e5b32c124cfa962f45e4d128e4a32210f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778203"
---
# <a name="summary-view---sampling-data"></a>Souhrnné zobrazení – vzorkovací data
Souhrnné zobrazení zobrazuje informace o nejvíce výkon-nákladné funkce v profilování spustit. Další informace, včetně popisu odkazů na oznámení a seznamů sestav, naleznete v [tématu Souhrnné zobrazení](../profiling/summary-view.md).

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="timeline-graph"></a>Graf časové osy
 Graf časové osy v souhrnném zobrazení zobrazuje procento využití procesoru (CPU) profilované aplikace v době, kdy došlo k profilování. Graf časové osy můžete použít k filtrování zobrazení na vybrané časové rozpětí. Další informace naleznete v [tématu Postup: Filtrování zobrazení sestavy z časové osy souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="hot-path"></a>Horká cesta
 **Horká cesta** zobrazuje cestu spuštění, ve kterém byla shromážděna většina vzorků. Klepnutím na funkci zobrazíte zobrazení Podrobnosti funkce pro funkci. Chcete-li zobrazit další zobrazení funkce, klepněte pravým tlačítkem myši na funkci a potom klepněte na zobrazení ze seznamu.

 **Horká cesta** obsahuje následující data pro každou funkci:

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název funkce.|
|**Včetně vzorků %**|Procento všech vzorků, ke kterým došlo při provádění této funkce nebo funkce volané touto funkcí.|
|**Exkluzivní vzorky %**|Procento všech vzorků, ke kterým došlo při provádění funkce kódu v těle funkce. Vzorky odebrané ve funkcích volaných touto funkcí nejsou zahrnuty.|

## <a name="functions-doing-most-individual-work"></a>Funkce, které vykonávají většinu individuální práce
 **Funkce dělá většinu jednotlivé práce** seznam zobrazuje funkce, které mají největší počet výhradní vzorky v profilování spustit. Výhradní ukázka je přiřazena funkci, pokud funkce provádí vlastní kód při sběru vzorku. Výhradní vzorek není přiřazen funkci, pokud funkce volá jinou funkci při odběru vzorku. Velký počet výhradní vzorky označuje, že významný čas byl strávený v samotné funkce.

 Klepnutím na funkci zobrazíte zobrazení Podrobnosti funkce pro funkci. Chcete-li zobrazit další zobrazení funkce, klepněte pravým tlačítkem myši na funkci a potom klepněte na zobrazení ze seznamu.

 **Funkce, které vykonávají většinu individuální práce,** obsahují následující data pro každou funkci:

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název funkce.|
|**Exkluzivní vzorky %**|Procento všech vzorků v profilování spustit, které byly shromážděny při spuštění funkce kódu v jeho těle funkce. Procento vylučuje vzorky, které byly shromážděny při provádění funkcí, které tato funkce volala.|

## <a name="see-also"></a>Viz také
- [Souhrnné zobrazení – data paměti .NET](../profiling/summary-view-dotnet-memory-data.md)
- [Souhrnné zobrazení - data instrumentace](../profiling/summary-view-instrumentation-data.md)
