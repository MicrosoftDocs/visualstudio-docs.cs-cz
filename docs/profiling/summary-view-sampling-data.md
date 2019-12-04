---
title: Souhrnné zobrazení – data vzorkování | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778203"
---
# <a name="summary-view---sampling-data"></a>Souhrnné zobrazení – vzorkování dat
V souhrnném zobrazení se zobrazí informace o nejdražších funkcích, které je náročné při spuštění profilace. Další informace, včetně popisu odkazů na oznámení a seznamů sestav, najdete v tématu [souhrnné zobrazení](../profiling/summary-view.md).

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="timeline-graph"></a>Graf časové osy
 Graf časové osy v zobrazení souhrnu zobrazuje procento využití procesoru profilované aplikace v době, kdy k profilaci došlo. Graf časové osy můžete použít k filtrování zobrazení do vybraného časového rozsahu. Další informace najdete v tématu [Postup: filtrování zobrazení sestav na časové ose souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="hot-path"></a>Kritická cesta
 **Cesta Hot** zobrazuje cestu spuštění, ve které bylo shromážděno více vzorků. Kliknutím na funkci můžete zobrazit zobrazení podrobností funkce pro danou funkci. Chcete-li zobrazit další zobrazení funkce, klikněte pravým tlačítkem myši na funkci a potom klikněte na zobrazení v seznamu.

 **Cesta Hot** obsahuje následující data pro každou funkci:

|Sloupec|Popis|
|------------|-----------------|
|**Jméno**|Název funkce|
|**% Včetně vzorků**|Procento všech vzorků, k nimž došlo při provádění této funkce nebo funkce volané touto funkcí|
|**% Exkluzivních vzorků**|Procentuální podíl všech vzorků, k nimž došlo v případě, že funkce prováděla kód v těle funkce. Vzorky shromážděné ve funkcích volaných touto funkcí nejsou zahrnuty.|

## <a name="functions-doing-most-individual-work"></a>Funkce provádějící většinu individuálních prací
 Funkce, které **provádějí většinu jednotlivých pracovních** seznamů, zobrazí funkce, které mají nejvyšší počet exkluzivních vzorků v průběhu profilace. Exkluzivní vzorek je přiřazen funkci, pokud funkce spouští svůj vlastní kód při shromáždění ukázky. Exkluzivní vzorek není přiřazen funkci, pokud funkce volá jinou funkci při shromáždění ukázky. Velký počet exkluzivních vzorků indikuje, že v samotné funkci se strávil značný čas.

 Kliknutím na funkci můžete zobrazit zobrazení podrobností funkce pro danou funkci. Chcete-li zobrazit další zobrazení pro tuto funkci, klikněte na ni pravým tlačítkem myši a potom klikněte na zobrazení v seznamu.

 **Funkce, které provádějí většinu individuální práce** , zahrnují následující data pro každou funkci:

|Sloupec|Popis|
|------------|-----------------|
|**Jméno**|Název funkce|
|**% Exkluzivních vzorků**|Procentuální podíl všech vzorků v běhu profilování, které byly shromážděny v případě, že funkce prováděla kód v těle funkce. Procento vyloučí vzorky, které byly shromážděny v případě, že byly spuštěny funkce, které tato funkce volala.|

## <a name="see-also"></a>Viz také:
- [Souhrnné zobrazení – data paměti .NET](../profiling/summary-view-dotnet-memory-data.md)
- [Souhrnné zobrazení – data instrumentace](../profiling/summary-view-instrumentation-data.md)
