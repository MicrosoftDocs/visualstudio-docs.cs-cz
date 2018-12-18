---
title: Zobrazení se souhrnnými | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdacfcba18d465685053cdea4581a5806c25db9d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757318"
---
# <a name="summary-view"></a>Souhrnné zobrazení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Souhrnné zobrazení zobrazuje informace o výkonu – nejdražší funkce nebo objekty během spuštění profilování. Toto zobrazení obsahuje graf časové osy a nejmíň dva seznamy nejdražší funkce nebo objekty založené na metodě profilování metriky výkonu. Data v tomto zobrazení, závisí na metodě profilování, která byla použita (vzorkování, instrumentace nebo souběžnosti) a určuje, zda byl shromážděn alokaci paměti .NET.  
  
 Pro všechny souhrnné zobrazení s výjimkou souhrnné zobrazení dat o souběžnosti časová osa grafu v souhrnném zobrazení ukazuje využití procesoru (CPU) profilované aplikace v čase, které profilaci došlo k chybě.  
  
-   Pokud zadáte část času v grafu, můžete znovu analyzovat data pro tento segment nebo zvětšete si zobrazení časové osy na segment, který jste zadali. Další informace najdete v tématu [postupy: filtrování zobrazení sestav ze časová osa souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)  
  
-   Můžete kliknout na funkci v seznamu souhrnné zobrazení otevřete zobrazení detailů funkce pro funkci. Můžete také můžete kliknout pravým tlačítkem funkce pro další možnosti zobrazení.  
  
-   Chcete-li změnit počet položek, které se objeví v zobrazení se souhrnnými seznamech, otevřete **nástroje** nabídky, přejděte k **možnosti**a potom klikněte na tlačítko **nástroje pro měření výkonu**. V části **obecné nastavení**, upravte **počet funkcí v souhrnném zobrazení** nastavení.  
  
## <a name="notifications-links"></a>Oznámení odkazy  
 Můžete kliknout na odkazy v seznamu oznámení k nastavení možností zobrazení sestavy. Seznam je napravo od grafu časové osy.  
  
|||  
|-|-|  
|**Zobrazení kódu nepocházejícího od uživatele**<br /><br /> **Zobrazit jen můj kód**|Není k dispozici, pro nativní kód nebo pro data profilace, která byla shromážděna pomocí metody instrumentace. Přepíná mezi zobrazením jenom data z uživatelského kódu (**zobrazit pouze můj kód**) a zobrazení dat v rámci veškerého kódu, včetně systému kódu (**zobrazit Neuživatelský kód**). Ve výchozím nastavení data jsou omezená na uživatelský kód. Chcete-li změnit nastavení, [postupy: filtrování profilování nástroje zobrazení sestav k zobrazení pouze můj kód](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|  
|**Zobrazit pokyny**|Zobrazí upozornění pravidel výkonu v **seznam chyb** okna. Další informace najdete v tématu [použití pravidel výkonu k analýze dat](../profiling/using-performance-rules-to-analyze-data.md)|  
  
## <a name="report"></a>Sestava  
 Můžete kliknout na odkazy v seznamu sestav otevřete různá zobrazení a k porovnání, uložte nebo filtrování sestavy. Seznam je napravo od grafu časové osy.  
  
|||  
|-|-|  
|**Zobrazit oříznutý strom volání**|Nejdražší cesty spuštění se zobrazí v zobrazení stromu volání. Další informace najdete v tématu [zobrazení stromu volání](../profiling/call-tree-view.md).|  
|**Zobrazit kritické řádky**|Není k dispozici pro profilaci dat, která byla shromážděna pomocí metody instrumentace. Nejdražší řádky zdrojového kódu se zobrazí v zobrazení řádků. Další informace najdete v tématu [zobrazení řádků](../profiling/lines-view.md).|  
|**Porovnat sestavy**|Zobrazí **vybrat soubory analýzy k porovnání** dialogovému oknu, kde můžete určit jiný soubor dat profilování má být porovnán s aktuální soubor. Další informace najdete v tématu [porovnávání datových souborů výkonu](../profiling/comparing-performance-data-files.md).|  
|**Export dat sestavy**|Zobrazí **Export sestavy** dialogovému oknu, kde můžete určit jeden nebo více zobrazení sestav pro uložení jako hodnoty oddělené čárkou (CSV) nebo soubory XML. Další informace najdete v tématu [postupy: Export sestav nástrojů pro profilaci](http://msdn.microsoft.com/en-us/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Uložit analyzovanou sestavu**|Uloží aktuální soubor dat profilování jako .vsps soubor, který otevře rychleji v rozhraní [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Další informace najdete v tématu [postupy: uložení analyzovat profilace datových souborů](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Filtrovat Data sestavy**|Zobrazí profilování podokna filtru sestavy, ve kterém můžete zadat kritéria k omezení dat v zobrazení sestav. Další informace najdete v tématu [filtr zobrazení sestav výkonu](../profiling/performance-report-view-filter.md)|  
|**Přepnout režim celé obrazovky**|Přepíná režim celé obrazovky pro zobrazení sestavy.|  
  
## <a name="see-also"></a>Viz také  
 [Souhrnné zobrazení](../profiling/summary-view-sampling-data.md)   
 [Souhrnné zobrazení](../profiling/summary-view-instrumentation-data.md)   
 [Souhrnné zobrazení](../profiling/summary-view-dotnet-memory-data.md)



