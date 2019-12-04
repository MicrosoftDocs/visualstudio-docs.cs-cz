---
title: Souhrnné zobrazení | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 87692c938462f166f93b4cfb8b223a45e2553ada
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74771571"
---
# <a name="summary-view"></a>Souhrnné zobrazení
V souhrnném zobrazení se zobrazí informace o nejdražších funkcích nebo objektech, které jsou v rámci profilování výkonné. Toto zobrazení obsahuje graf časové osy a dva nebo více seznamů nejdražších funkcí nebo objektů na základě metrik výkonu metody profilace. Data v tomto zobrazení závisí na metodě profilování, která byla použita (vzorkování, instrumentace nebo souběžnost) a na tom, zda bylo shromážděno přidělení paměti .NET.

 Pro všechna Souhrnná zobrazení, s výjimkou souhrnného zobrazení dat souběžnosti, se v grafu časové osy v souhrnném zobrazení zobrazuje využití procesoru profilované aplikace v době, kdy k profilaci došlo.

- Zadáte-li v grafu segment času, můžete znovu analyzovat data pro daný segment nebo zvětšit zobrazení časové osy na segment, který jste zadali. Další informace najdete v tématu [Postup: filtrování zobrazení sestav na časové ose souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

- Kliknutím na funkci v seznamu souhrnných zobrazení můžete otevřít zobrazení podrobností funkce pro funkci. Můžete také kliknout pravým tlačítkem na funkci pro další možnosti zobrazení.

- Chcete-li upravit počet položek, které se zobrazí v seznamu souhrnných zobrazení, otevřete nabídku **nástroje** , přejděte na **možnost možnosti**a klikněte na položku **Nástroje pro sledování výkonu**. V části **Obecná nastavení**upravte nastavení **počet funkcí v souhrnném zobrazení** .

## <a name="notifications-links"></a>Odkazy na oznámení
 Kliknutím na odkazy v seznamu oznámení můžete nastavit možnosti zobrazení sestavy. Seznam je napravo od grafu časové osy.

|||
|-|-|
|**Zobrazit kód nesouvisející s uživatelem**<br /><br /> **Zobrazit Pouze můj kód**|Není k dispozici pro nativní kód nebo pro data profilace, která byla shromážděna pomocí metody instrumentace. Přepíná mezi zobrazením pouze dat z uživatelského kódu (**zobrazit pouze můj kód**) a zobrazením dat ze všech kódů, včetně systémového kódu (**Zobrazit kód nesouvisející s uživatelem**). Ve výchozím nastavení jsou data omezena na uživatelský kód. Chcete-li změnit nastavení, přečtěte si téma [Postup: filtrování zobrazení sestav nástrojů pro profilaci pro zobrazení pouze můj kód](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|
|**Zobrazit doprovodné materiály**|Zobrazí upozornění pravidla výkonu v okně **Seznam chyb** . Další informace najdete v tématu [použití pravidel výkonu k analýze dat](../profiling/using-performance-rules-to-analyze-data.md) .|

## <a name="report"></a>Sestava
 Kliknutím na odkazy v seznamu sestavy otevřete různá zobrazení a můžete sestavu porovnat, Uložit nebo filtrovat. Seznam je napravo od grafu časové osy.

| | |
|----------------------------| - |
| **Zobrazit oříznutý strom volání** | Zobrazí nejdražších cest spuštění v zobrazení stromu volání. Další informace naleznete v tématu [zobrazení stromu volání](../profiling/call-tree-view.md). |
| **Zobrazit horké řádky** | Není k dispozici pro data profilace, která byla shromážděna pomocí metody instrumentace. Zobrazí nejlevnější řádky zdrojového kódu v zobrazení řádků. Další informace najdete v tématu [zobrazení řádků](../profiling/lines-view.md). |
| **Porovnání sestav** | Zobrazí dialogové okno **Vybrat soubory analýzy pro porovnání** , kde můžete určit jiný soubor dat profilování pro porovnání s aktuálním souborem. Další informace najdete v tématu [porovnání datových souborů výkonu](../profiling/comparing-performance-data-files.md). |
| **Exportovat data sestavy** | Zobrazí dialogové okno **exportovat sestavu** , ve kterém můžete zadat jedno nebo více zobrazení sestav k uložení jako textový soubor s oddělovači (. csv) nebo soubory. XML. Další informace najdete v tématu [Postup: Export sestav nástrojů pro profilaci](/previous-versions/visualstudio/visual-studio-2010/ms182394\(v\=vs.100\)). |
| **Uložit analyzovanou sestavu** | Uloží aktuální soubor dat profilování jako soubor. vsps, který se v rozhraní pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]otevře rychleji. Další informace najdete v tématu [Postup: uložení analyzovaných datových souborů profilování](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\)). |
| **Filtrovat data sestavy** | Zobrazí podokno filtru sestavy profilace, kde můžete zadat kritéria pro omezení dat v zobrazení sestavy. Další informace najdete v tématu [Filtr zobrazení sestav výkonu.](../profiling/performance-report-view-filter.md) |
| **Přepnout na celou obrazovku** | Přepne režim celé obrazovky pro zobrazení sestavy. |

## <a name="see-also"></a>Viz také:
- [Souhrnné zobrazení – vzorkování dat](../profiling/summary-view-sampling-data.md)
- [Souhrnné zobrazení – data instrumentace](../profiling/summary-view-instrumentation-data.md)
- [Souhrnné zobrazení – data paměti .NET](../profiling/summary-view-dotnet-memory-data.md)
