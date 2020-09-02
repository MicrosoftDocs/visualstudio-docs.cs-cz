---
title: VSInstr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fc68ad7da06a1710e3c34ddb601155fc3d0b1182
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330505"
---
# <a name="vsinstr"></a>VSInstr
Nástroj VSInstr slouží k instrumentaci binárních souborů. Je vyvolána pomocí následující syntaxe:

```cmd
VSInstr [/U] filename [/options]
```

 Následující tabulka popisuje možnosti nástroje VSInstr:

|Možnosti|Popis|
|-------------|-----------------|
|**Pomáhat** nebo **?**|Zobrazí pomocníka.|
|**U**|Zapíše výstup přesměrované konzoly jako Unicode. Je nutné zadat první možnost.|
|`@filename`|Určuje název souboru odpovědí, který obsahuje jednu možnost příkazu na řádek.  Nepoužívejte uvozovky.|
|**OutputPath**`:path`|Určuje cílový adresář pro instrumentované bitové kopie. Pokud není zadána výstupní cesta, původní binární soubor byl přejmenován připojením "orig" k názvu souboru ve stejném adresáři a kopie binárního souboru je instrumentovaná.|
|**Vyloučit:**`funcspec`|Určuje specifikaci funkce, která se má vyloučit z instrumentace pomocí sond. To je užitečné v případě, že při vkládání testu sondy do funkce dojde k nepředvídatelným nebo nežádoucím výsledkům.<br /><br /> Nepoužívejte možnosti **Exclude** a **include** , které odkazují na funkce ve stejném binárním souboru.<br /><br /> Můžete zadat více specifikací funkcí s oddělenými možnostmi **vyloučení** .<br /><br /> `funcspec` je definován jako:<br /><br /> [obor názvů \<separator1> ] [třída \<separator2> ] slouží<br /><br /> \<separator1> je určena `::` pro nativní kód a `.` pro spravovaný kód.<br /><br /> \<separator2> je vždycky `::`.<br /><br /> **Vyloučení** je podporováno s pokrytím kódu.<br /><br /> Zástupný znak \* je podporován. Například pro vyloučení všech funkcí v oboru názvů použijte:<br /><br /> MyNamespace::\*<br /><br /> K vypsání úplných názvů funkcí v zadaném binárním souboru můžete použít **VSInstr/DumpFuncs** .|
|**Zahrnout:**`funcspec`|Určuje specifikace funkce v binárním souboru pro instrumentaci s sondami. Všechny ostatní funkce v binárních souborech nejsou instrumentované.<br /><br /> Můžete zadat více specifikací funkcí s oddělenými možnostmi **zahrnutí** .<br /><br /> Nepoužívejte možnosti **include** a **Exclude** , které odkazují na funkce ve stejném binárním souboru.<br /><br /> **Zahrnutí** není podporováno s pokrytím kódu.<br /><br /> `funcspec` je definován jako:<br /><br /> [obor názvů \<separator1> ] [třída \<separator2> ] slouží<br /><br /> \<separator1> je určena `::` pro nativní kód a `.` pro spravovaný kód.<br /><br /> \<separator2> je vždycky `::`.<br /><br /> Zástupný znak \* je podporován. Například pro zahrnutí všech funkcí do oboru názvů použijte:<br /><br /> MyNamespace::\*<br /><br /> K vypsání úplných názvů funkcí v zadaném binárním souboru můžete použít **VSInstr/DumpFuncs** .|
|**DumpFuncs**|Zobrazí seznam funkcí v rámci zadaného obrázku. Není prováděna žádná instrumentace.|
|**ExcludeSmallFuncs**|Vyloučí malé funkce, což jsou krátké funkce, které nedělají žádná volání funkcí, od instrumentace. Možnost **ExcludeSmallFuncs** poskytuje méně zátěže instrumentace a tím zvýšila rychlost instrumentace.<br /><br /> Vyloučení malých funkcí také snižuje. velikost souboru *VSP* a čas potřebný k analýze.|
|**Označit:**{**before** \| **po** \| **horní** \| **části**}`,funcname,markid`|Vloží značku profilu (identifikátor používaný k vymezení dat v sestavách), které můžete použít k identifikaci počátečního nebo koncového rozsahu dat v souboru sestavy. vsp.<br /><br /> **Před** – bezprostředně před cílovou položkou funkce.<br /><br /> **After** hned po ukončení cílové funkce.<br /><br /> **Nahoru** a hned za cílovou položkou funkce.<br /><br /> **Zdola** – těsně před každým návratem v cílové funkci.<br /><br /> `funcname` – Název cílové funkce<br /><br /> `Markid` – Kladné celé číslo (Long), které se použije jako identifikátor značky Profile.|
|**Pokrytí**|Provede instrumentaci pokrytí. Dá se použít jenom s následujícími možnostmi: **verbose**, **OutputPath**, **Exclude**a **logfile**..|
|**Podrobné**|Možnost **verbose** se používá k zobrazení podrobných informací o procesu instrumentace.|
|**Upozornit**`[:[Message Number[;Message Number]]]`|Potlačí všechna nebo konkrétní upozornění.<br /><br /> `Message Number` – číslo upozornění. Pokud `Message Number` je tento parametr vynechán, budou potlačena všechna upozornění.<br /><br /> Další informace naleznete v tématu [VSInstr Warnings](../profiling/vsinstr-warnings.md).|
|**Ovládací prvek:** `{` **Podproces** \| **Zpracování** \| **Globální**`}`|Určuje úroveň profilace následujících možností řízení sběru dat VSInstr:<br /><br /> **Zahájení**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread** – určuje funkce ovládacího prvku shromažďování dat na úrovni vlákna. Profilace je spuštěná nebo zastavená jenom pro aktuální vlákno. Stav profilace jiných vláken není ovlivněn. Výchozím nastavením je vlákno.<br /><br /> **Proces** – určuje funkce ovládacího prvku shromažďování dat profilování na úrovni procesu. Profilace se spouští nebo zastavuje pro všechna vlákna v aktuálním procesu. Stav profilace jiných procesů není ovlivněn.<br /><br /> **Global** – určuje funkce ovládacího prvku shromažďování dat globální úrovně (mezi procesy).<br /><br /> Pokud nezadáte úroveň profilace, dojde k chybě.|
|**Začátek:** `{` **Uvnitř** \| **Mimo rámec**`},funcname`|Omezí shromažďování dat na cílovou funkci a podřízené funkce volané touto funkcí.<br /><br /> **Uvnitř** – vloží funkci StartProfile hned za položku do cílové funkce. Vloží funkci StopProfile těsně před každou vrácenou cílovou funkcí.<br /><br /> **Mimo** – vloží funkci StartProfile těsně před každé volání cílové funkce. Vloží funkci StopProfile hned po každém volání cílové funkce.<br /><br /> `funcname` – název cílové funkce.|
|**Pozastavit:** `{` **Uvnitř** \| **Mimo rámec**`},funcname`|Vyloučí shromažďování dat pro cílovou funkci a podřízené funkce volané funkcí.<br /><br /> **Uvnitř** – vloží funkci SuspendProfile hned za položku do cílové funkce. Vloží funkci ResumeProfile těsně před každou vrácenou cílovou funkcí.<br /><br /> **Mimo** – vloží funkci SuspendProfile těsně před vstup do cílové funkce. Vloží funkci ResumeProfile hned po ukončení z cílové funkce.<br /><br /> `funcname` – název cílové funkce<br /><br /> Pokud cílová funkce obsahuje funkci StartProfile, je před ní vložena funkce SuspendProfile. Pokud cílová funkce obsahuje funkci StopProfile, je po ní vložena funkce ResumeProfile.|
|**StartOnly:** `{` **Před** \| **Po** \| **Horní část** \| **Dolní část**`},funcname`|Zahájí shromažďování dat během běhu profilace. Vloží funkci rozhraní API StartProfile v zadaném umístění.<br /><br /> **Před** – bezprostředně před cílovou položkou funkce.<br /><br /> **After** hned po ukončení cílové funkce.<br /><br /> **Nahoru** a hned za cílovou položkou funkce.<br /><br /> **Zdola** – těsně před každým návratem v cílové funkci.<br /><br /> `funcname` – název cílové funkce|
|**StopOnly:**{**before** \| **po** \| **horní** \| **části**}`,funcname`|Zastavuje shromažďování dat během běhu profilace. Vloží funkci StopProfile do zadaného umístění.<br /><br /> **Před** – bezprostředně před cílovou položkou funkce.<br /><br /> **After** hned po ukončení cílové funkce.<br /><br /> **Nahoru** a hned za cílovou položkou funkce.<br /><br /> **Zdola** – těsně před každým návratem v cílové funkci.<br /><br /> `funcname` – název cílové funkce|
|**SuspendOnly:**{**before** \| **po** \| **horní** \| **části**}`,funcname`|Zastavuje shromažďování dat během běhu profilace. Vloží rozhraní API SuspendProfile v zadaném umístění.<br /><br /> **Před** – bezprostředně před cílovou položkou funkce.<br /><br /> **After** hned po ukončení cílové funkce.<br /><br /> **Nahoru** a hned za cílovou položkou funkce.<br /><br /> **Zdola** – těsně před každým návratem v cílové funkci.<br /><br /> `funcname` – název cílové funkce<br /><br /> Pokud cílová funkce obsahuje funkci StartProfile, je před ní vložena funkce SuspendProfile.|
|**ResumeOnly:**{**before** \| **po** \| **horní** \| **části**}`,funcname`|Spustí nebo obnoví shromažďování dat během běhu profilace.<br /><br /> Obvykle se používá ke spuštění profilování poté, co možnost **SuspendOnly** zastaví profilování. Vloží rozhraní ResumeProfile API v zadaném umístění.<br /><br /> **Před** – bezprostředně před cílovou položkou funkce.<br /><br /> **After** hned po ukončení cílové funkce.<br /><br /> **Nahoru** a hned za cílovou položkou funkce.<br /><br /> **Zdola** – těsně před každým návratem v cílové funkci.<br /><br /> `funcname` – název cílové funkce<br /><br /> Pokud cílová funkce obsahuje funkci StopProfile, je po ní vložena funkce ResumeProfile.|

## <a name="see-also"></a>Viz také
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Upozornění VSInstr](../profiling/vsinstr-warnings.md)
- [Zobrazení sestav výkonu](../profiling/performance-report-views.md)
