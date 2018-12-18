---
title: Nástroj VSInstr | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, instrumentation
- instrumentation, VSInstr tool
- profiling tools,VSInstr
- command-line tools, instrumentation
- command line, tools
- VSInstr
- VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2526938274299cc5a90319749531f80e8bd3a90d
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220544"
---
# <a name="vsinstr"></a>VSInstr
Nástroj VSInstr se používá k instrumentaci binárních souborů. Vyvolá se pomocí následující syntaxe:  
  
```cmd  
VSInstr [/U] filename [/options]  
```  
  
 Následující tabulka popisuje možnosti nástroje VSInstr:  
  
|Možnosti|Popis|  
|-------------|-----------------|  
|**Nápověda** nebo **?**|Zobrazí nápovědu.|  
|**U**|Přesměrovaný výstup konzoly zapíše jako kódování Unicode. Musí být zadána první možnost.|  
|`@filename`|Určuje název souboru odpovědí, který obsahuje každý řádek jednou z možností příkazu.  Nepoužívejte uvozovky.|  
|**OutputPath** `:path`|Určuje cílový adresář pro instrumentovanou bitovou kopii. Pokud není zadaná výstupní cesta, původní binární soubor je přejmenována přidáním "Orig" název souboru ve stejném adresáři a instrumentovaná kopie binárního souboru.|  
|**Vyloučení** `:funcspec`|Určuje specifikaci funkce vyloučit z instrumentace podle sondy. Je užitečné při profilaci testu vložení ve funkci způsobí, že výsledky nepředvídatelné nebo nežádoucí.<br /><br /> Nepoužívejte **vyloučit** a **zahrnout** možnosti, které odkazují na funkce do stejného binárního souboru.<br /><br /> Můžete zadat více specifikaci funkce samostatné **vyloučit** možnosti.<br /><br /> `funcspec` je definované jako:<br /><br /> [obor názvů\<separator1 >] [třída\<separator2 >] – funkce<br /><br /> \<separator1 > je `::` pro nativní kód a `.` pro spravovaný kód.<br /><br /> \<separator2 > je vždy `::`<br /><br /> **Vyloučit** se podporuje s pokrytím kódu.<br /><br /> Zástupný znak \* je podporována. Chcete-li například vyloučení všech funkcí v oboru názvů, použijte:<br /><br /> MyNamespace::\*<br /><br /> Můžete použít **VSInstr /DumpFuncs** do seznamu dokončení názvů funkcí v zadané binární soubor.|  
|**Zahrnout** `:funcspec`|Určuje specifikaci funkce v binárním souboru instrumentovat s testy. Všechny funkce v binárních souborech nejsou podporovány.<br /><br /> Můžete zadat více specifikací funkcí rozsahové samostatné **zahrnout** možnosti.<br /><br /> Nepoužívejte **zahrnout** a **vyloučit** možnosti, které odkazují na funkce do stejného binárního souboru.<br /><br /> **Zahrnout** není podporován s pokrytím kódu.<br /><br /> `funcspec` je definované jako:<br /><br /> [obor názvů\<separator1 >] [třída\<separator2 >] – funkce<br /><br /> \<separator1 > je `::` pro nativní kód a `.` pro spravovaný kód.<br /><br /> \<separator2 > je vždy `::`<br /><br /> Zástupný znak \* je podporována. Chcete-li například zahrnují všechny funkce v oboru názvů, použijte:<br /><br /> MyNamespace::\*<br /><br /> Můžete použít **VSInstr /DumpFuncs** do seznamu dokončení názvů funkcí v zadané binární soubor.|  
|**DumpFuncs**|Seznam funkcí v rámci zadané bitové kopie. Není provedena žádná instrumentace.|  
|**ExcludeSmallFuncs**|Vyloučí malé funkce, které jsou krátkých funkcí, které Nedovolte, aby byly všechny volání funkcí z instrumentace. **ExcludeSmallFuncs** poskytuje možnost pro menší nároky na instrumentace se tak lepší instrumentace rychlostí.<br /><br /> Vyloučení malé funkce také snižuje požadavek. *vsp* velikost a čas potřebný pro analýzu souborů.|  
|**Značka:**{**před**`&#124;`**po**`&#124;`**horní**`&#124;`**dolní**}`,funcname,markid`|Vloží značku profilu (identifikátor používaný k oddělení dat v sestavách), můžete použít k identifikaci počáteční nebo koncová hodnota rozsahu dat v sestavě souboru .vsp.<br /><br /> **Před** – bezprostředně před cílovou položkou funkce.<br /><br /> **Po** – ihned po ukončení funkce cíl.<br /><br /> **Horní** – okamžitě za cílovou položkou funkce.<br /><br /> **Dolní** – bezprostředně před každou vrácení cílová funkce.<br /><br /> `funcname` – Název cílové – funkce<br /><br /> `Markid` -Kladné celé číslo (dlouhé) použít jako identifikátor značky profilu.|  
|**Pokrytí**|Provádí instrumentaci pokrytí. Je možné jenom s těmito možnostmi: **Verbose**, **OutputPath**, **vyloučit**, a **Logfile**...|  
|**Verbose**|**Verbose** možnost se používá k zobrazení podrobných informací o procesu instrumentace.|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|Potlačit všechny nebo specifická upozornění.<br /><br /> `Message Number` -číslo upozornění. Pokud `Message Number` je tento parametr vynechán, jsou potlačeny všechny výstrahy.<br /><br /> Další informace najdete v tématu [upozornění VSInstr](../profiling/vsinstr-warnings.md).|  
|**Ovládací prvek** `:{` **vlákna** `&#124;` **procesu** `&#124;` **globální** `}`|Určuje úroveň profilování následující kolekci dat VSInstr řídit možnosti:<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Vlákno** -určuje funkce ovládacího prvku kolekce dat na úrovni vlákna. Profilace spuštěna nebo zastavena pouze pro aktuální vlákno. Profilace stavu ostatní vlákna nemá vliv. Výchozí hodnota je vlákno.<br /><br /> **Proces** -určuje funkce ovládacího prvku kolekce profilování dat úrovni procesu. Profilace spuštění nebo zastavení pro všechna vlákna v aktuálním procesu. Profilace stav dalších procesů nemá vliv.<br /><br /> **Globální** -určuje funkce ovládacího prvku kolekce dat (napříč procesy) na globální úrovni.<br /><br /> Pokud nezadáte profilování úroveň dojde k chybě.|  
|**Spustit** `:{` **uvnitř** `&#124;` **mimo** `},funcname`|Omezení shromažďování dat pro funkci cíl a podřízené funkce volané funkce.<br /><br /> **Uvnitř** – vloží StartProfile funkce hned po položce, aby cílová funkce. Vloží funkci StopProfile bezprostředně před každou vrátit cílová funkce.<br /><br /> **Mimo** – vloží funkci StartProfile bezprostředně před všechna volání cílová funkce. Vloží StopProfile funkce hned po každé volání cílová funkce.<br /><br /> `funcname` -Název cílová funkce.|  
|**Pozastavit** `:{` **uvnitř** `&#124;` **mimo** `},funcname`|Vyloučí shromažďování dat pro cílová funkce a podřízené funkce volané funkce.<br /><br /> **Uvnitř** – vloží SuspendProfile funkce hned po položce, aby cílová funkce. Vloží funkci ResumeProfile bezprostředně před každou vrátit cílová funkce.<br /><br /> **Mimo** – vloží funkci SuspendProfile bezprostředně před vstupem do této funkce cíl. Vloží ResumeProfile funkce hned po opuštění cílová funkce.<br /><br /> `funcname` -Název cílová funkce.<br /><br /> Pokud cílová funkce obsahuje StartProfile funkce, funkce SuspendProfile vložena před ní. Pokud cílová funkce obsahuje StopProfile funkce, funkce ResumeProfile vložena za ním.|  
|**StartOnly:** `{` **před** `&#124;` **po** `&#124;` **horní** `&#124;` **dolní** `},funcname`|Spustí shromažďování dat během spuštění profilování. V zadaném umístění vloží funkci StartProfile rozhraní API.<br /><br /> **Před** – bezprostředně před cílovou položkou funkce.<br /><br /> **Po** – ihned po ukončení funkce cíl.<br /><br /> **Horní** – okamžitě za cílovou položkou funkce.<br /><br /> **Dolní** – bezprostředně před každou vrácení cílová funkce.<br /><br /> `funcname` -Název cílová funkce.|  
|**StopOnly:**{**před**`&#124;`**po**`&#124;`**horní**`&#124;`**dolní**}`,funcname`|Zastaví shromažďování dat během spuštění profilování. Vloží funkci StopProfile v zadaném umístění.<br /><br /> **Před** – bezprostředně před cílovou položkou funkce.<br /><br /> **Po** – ihned po ukončení funkce cíl.<br /><br /> **Horní** – okamžitě za cílovou položkou funkce.<br /><br /> **Dolní** – bezprostředně před každou vrácení cílová funkce.<br /><br /> `funcname` -Název cílová funkce.|  
|**SuspendOnly:**{**před**`&#124;`**po**`&#124;`**horní**`&#124;`**dolní**}`,funcname`|Zastaví shromažďování dat během spuštění profilování. V zadaném umístění vloží SuspendProfile rozhraní API.<br /><br /> **Před** – bezprostředně před cílovou položkou funkce.<br /><br /> **Po** – ihned po ukončení funkce cíl.<br /><br /> **Horní** – okamžitě za cílovou položkou funkce.<br /><br /> **Dolní** – bezprostředně před každou vrácení cílová funkce.<br /><br /> `funcname` -Název cílová funkce.<br /><br /> Pokud cílová funkce obsahuje StartProfile funkce, funkce SuspendProfile vložena před ní.|  
|**ResumeOnly:**{**před**`&#124;`**po**`&#124;`**horní**`&#124;`**dolní**}`,funcname`|Spustí nebo obnoví shromažďování dat během spuštění profilování.<br /><br /> Obvykle se používá k zahájení profilace, až **SuspendOnly** možnost zastavil profilace. V zadaném umístění vloží ResumeProfile API.<br /><br /> **Před** – bezprostředně před cílovou položkou funkce.<br /><br /> **Po** – ihned po ukončení funkce cíl.<br /><br /> **Horní** – okamžitě za cílovou položkou funkce.<br /><br /> **Dolní** – bezprostředně před každou vrácení cílová funkce.<br /><br /> `funcname` -Název cílová funkce.<br /><br /> Pokud cílová funkce obsahuje StopProfile funkce, funkce ResumeProfile vložena za ním.|  
  
## <a name="see-also"></a>Viz také:  
 [Vsperfmon –](../profiling/vsperfmon.md)   
 [Nástroj VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Upozornění VSInstr](../profiling/vsinstr-warnings.md)   
 [Zobrazení sestav výkonu](../profiling/performance-report-views.md)