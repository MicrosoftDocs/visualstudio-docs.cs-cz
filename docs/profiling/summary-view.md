---
title: Souhrnné zobrazení | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771571"
---
# <a name="summary-view"></a>Souhrnné zobrazení
Souhrnné zobrazení zobrazuje informace o nejvíce výkon-nákladné funkce nebo objekty v profilování spustit. Toto zobrazení poskytuje graf časové osy a dva nebo více seznamů nejdražších funkcí nebo objektů na základě metrik výkonu metody profilování. Data v tomto zobrazení závisí na metodě profilování, která byla použita (vzorkování, instrumentace nebo souběžnost) a zda bylo shromážděno přidělení paměti .NET.

 Pro všechna souhrnná zobrazení s výjimkou souhrnného zobrazení dat souběžnosti zobrazuje graf časové osy v souhrnném zobrazení využití procesoru (CPU) profilované aplikace v době, kdy došlo k profilování.

- Pokud v grafu zadáte časový úsek, můžete data pro daný segment znovu analyzovat nebo zvětšit zobrazení časové osy na zadaný segment. Další informace naleznete v [tématu Postup: Filtrování zobrazení sestavy z časové osy souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

- Klepnutím na funkci v seznamu Souhrnné zobrazení otevřete zobrazení Podrobnosti funkce pro funkci. Můžete také klepnout pravým tlačítkem myši na funkci pro další možnosti zobrazení.

- Chcete-li změnit počet položek, které se zobrazí v seznamech souhrnných zobrazení, otevřete nabídku **Nástroje,** přejděte na **příkaz Možnosti**a klepněte na příkaz **Nástroje výkonu**. V části **Obecné nastavení**upravte nastavení Počet funkcí **v souhrnném zobrazení.**

## <a name="notifications-links"></a>Odkazy na oznámení
 Kliknutím na odkazy v seznamu Oznámení můžete nastavit možnosti zobrazení sestavy. Seznam je napravo od grafu časové osy.

|||
|-|-|
|**Zobrazit neuživatelský kód**<br /><br /> **Zobrazit pouze můj kód**|Není k dispozici pro nativní kód nebo pro profilování dat, která byla shromážděna pomocí metody instrumentace. Přepíná mezi zobrazením pouze dat z uživatelského kódu **(Zobrazit pouze můj kód)** a zobrazením dat ze všech kódů, včetně systémového kódu **(Zobrazit neuživatelský kód).** Ve výchozím nastavení jsou data omezena na uživatelský kód. Pokud chcete toto nastavení změnit, přečtěte si informace o tom, [jak: Filtrovat zobrazení sestavy nástrojů profilování tak, aby se zobrazila pouze můj kód](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|
|**Zobrazit pokyny**|Zobrazí upozornění na pravidla výkonu v okně **Seznam chyb.** Další informace naleznete v [tématu Použití pravidel výkonu k analýze dat.](../profiling/using-performance-rules-to-analyze-data.md)|

## <a name="report"></a>Sestava
 Kliknutím na odkazy v seznamu Sestava můžete otevřít různá zobrazení a sestavu porovnat, uložit nebo filtrovat. Seznam je napravo od grafu časové osy.

| | |
|----------------------------| - |
| **Zobrazit oříznutý strom volání** | Zobrazí nejdražší cesty spuštění v zobrazení stromu volání. Další informace naleznete v tématu [Strom volání zobrazení](../profiling/call-tree-view.md). |
| **Zobrazit horké čáry** | Není k dispozici pro profilování dat, která byla shromážděna pomocí metody instrumentace. Zobrazí nejdražší řádky zdrojového kódu v zobrazení řádků. Další informace naleznete v [tématu Čáry zobrazení](../profiling/lines-view.md). |
| **Porovnat sestavy** | Zobrazí dialogové okno **Vybrat soubory analýzy pro porovnání,** ve kterém můžete zadat jiný datový soubor profilování, který chcete porovnat s aktuálním souborem. Další informace naleznete v [tématu Porovnání datových souborů výkonu](../profiling/comparing-performance-data-files.md). |
| **Exportovat data sestavy** | Zobrazí dialogové okno **Exportovat sestavu,** ve kterém můžete zadat jedno nebo více zobrazení sestavy, které chcete uložit jako hodnotu oddělenou čárkami (.csv) nebo XML. Další informace naleznete v [tématu Postup: Export sestav nástrojů profilování](/previous-versions/visualstudio/visual-studio-2010/ms182394\(v\=vs.100\)). |
| **Uložit analyzouženou sestavu** | Uloží aktuální datový soubor profilování jako soubor .vsps, který se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]v rozhraní pro rozhraní pro aplikace . Další informace naleznete v [tématu Postup: Uložení analyzovaných datových souborů profilování](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\)). |
| **Filtrovat data sestavy** | Zobrazí podokno filtru sestavy profilování, ve kterém můžete zadat kritéria pro omezení dat v zobrazení sestavy. Další informace naleznete v tématu [Sledování výkonu sestavy filtru](../profiling/performance-report-view-filter.md) |
| **Přepnout celou obrazovku** | Přepíná režim celé obrazovky pro zobrazení sestavy. |

## <a name="see-also"></a>Viz také
- [Souhrnné zobrazení – vzorkovací data](../profiling/summary-view-sampling-data.md)
- [Souhrnné zobrazení – data instrumentace](../profiling/summary-view-instrumentation-data.md)
- [Souhrnné zobrazení - data paměti .NET](../profiling/summary-view-dotnet-memory-data.md)
