---
title: VSInstr | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 386d81d14996547670944ce1b4911233eb9c8955
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779919"
---
# <a name="vsinstr"></a>VSInstr
Nástroj VSInstr se používá k instrumentaci binárních souborů. Je vyvolána pomocí následující syntaxe:

```cmd
VSInstr [/U] filename [/options]
```

 Následující tabulka popisuje možnosti nástroje VSInstr:

|Možnosti|Popis|
|-------------|-----------------|
|**Pomoc** nebo **?**|Zobrazí nápovědu.|
|**U**|Zapíše přesměrovaný výstup konzoly jako Unicode. Musí být zadána první možnost.|
|`@filename`|Určuje název souboru odpovědí, který obsahuje jednu možnost příkazu na řádek.  Nepoužívejte uvozovky.|
|**OutputPath**`:path`|Určuje cílový adresář pro instrumentovaný obraz. Pokud není zadána výstupní cesta, původní binární soubor je přejmenován připojením "Orig" k názvu souboru ve stejném adresáři a kopie binárního souboru je instrumentován.|
|**Exclude** `:funcspec`|Určuje specifikaci funkce, která má být vyloučena z instrumentace sondami. To je užitečné při profilování sondy vložení do funkce způsobuje nepředvídatelné nebo nežádoucí výsledky.<br /><br /> Nepoužívejte **možnosti Vyloučit** a **Zahrnout,** které odkazují na funkce ve stejném binárním souboru.<br /><br /> Můžete zadat více specifikací funkce se samostatnými možnostmi **Vyloučit.**<br /><br /> `funcspec`je definována jako:<br /><br /> [oddělovač oboru\<názvů1>] [oddělovač třídy2\<>]funkce<br /><br /> \<oddělovač1 `::`> je pro `.` nativní kód a pro spravovaný kód.<br /><br /> \<separátor2> je vždy`::`<br /><br /> **Vyloučení** je podporováno pokrytím kódu.<br /><br /> Zástupný znak \* je podporován. Chcete-li například vyloučit všechny funkce v oboru názvů, použijte:<br /><br /> Mynamespace::\*<br /><br /> Můžete použít **VSInstr /DumpFuncs** seznam úplných názvů funkcí v zadaném binárním souboru.|
|**Zařadit členy** `:funcspec`|Určuje specifikaci funkce v binárním objektu pro přístroj se sondami. Všechny ostatní funkce v binárních souborech nejsou instrumentované.<br /><br /> Můžete zadat více specifikací funkce se samostatnými možnostmi **Zahrnout.**<br /><br /> Nepoužívejte **možnosti Zahrnout** a **Vyloučit,** které odkazují na funkce ve stejném binárním souboru.<br /><br /> **Zahrnout** není podporováno s pokrytím kódu.<br /><br /> `funcspec`je definována jako:<br /><br /> [oddělovač oboru\<názvů1>] [oddělovač třídy2\<>]funkce<br /><br /> \<oddělovač1 `::`> je pro `.` nativní kód a pro spravovaný kód.<br /><br /> \<separátor2> je vždy`::`<br /><br /> Zástupný znak \* je podporován. Chcete-li například zahrnout všechny funkce do oboru názvů, použijte:<br /><br /> Mynamespace::\*<br /><br /> Můžete použít **VSInstr /DumpFuncs** seznam úplných názvů funkcí v zadaném binárním souboru.|
|**DumpFuncs**|Zobrazí seznam funkcí v zadaném obrázku. Není prováděna žádná instrumentace.|
|**VyloučitSmallFuncs**|Vyloučí malé funkce, což jsou krátké funkce, které neprovádějí volání žádné funkce z instrumentace. Možnost **ExcludeSmallFuncs** poskytuje menší nadzemní zařízení a tím i vylepšenou rychlost instrumentace.<br /><br /> Vyloučení malých funkcí také snižuje . velikost *souboru vsp* a čas potřebný pro analýzu.|
|**Značka:**{**Před**`&#124;`**Po**`&#124;`**horním**`&#124;`**dně**}`,funcname,markid`|Vloží značku profilu (identifikátor používaný k vymezení dat v sestavách), kterou můžete použít k identifikaci začátku nebo konce oblasti dat v souboru sestavy VSP.<br /><br /> **Před** - Bezprostředně před zadání matné funkce.<br /><br /> **Po** - Ihned po ukončení cílové funkce.<br /><br /> **Nahoře** - Bezprostředně po zadání cílové funkce.<br /><br /> **Dole** - Bezprostředně před každým návratem v cílové funkci.<br /><br /> `funcname`- Název cílové funkce<br /><br /> `Markid`- Kladné celé číslo (dlouhé) pro použití jako identifikátor značky profilu.|
|**Pokrytí**|Provádí instrumentaci pokrytí. Lze jej použít pouze s následujícími možnostmi: **Verbose**, **OutputPath**, **Exclude**a **Logfile**..|
|**Podrobné**|Možnost **Verbose** se používá k zobrazení podrobných informací o procesu instrumentace.|
|**NeVarovat**`[:[Message Number[;Message Number]]]`|Potlačit všechna nebo konkrétní upozornění.<br /><br /> `Message Number`- výstražné číslo. Pokud `Message Number` je vynechán, všechna upozornění jsou potlačeny.<br /><br /> Další informace naleznete v tématu [VSInstr Warnings](../profiling/vsinstr-warnings.md).|
|Globální **Global** **proces** `:{` `&#124;` **řídicího** **vlákna** `&#124;``}`|Určuje úroveň profilování následujících možností řízení shromažďování dat VSInstr:<br /><br /> **Zahájení**<br /><br /> **SpustitPouze**<br /><br /> **Suspend**<br /><br /> **ZastavitPouze**<br /><br /> **Pouze pozastavit**<br /><br /> **PokračovatOnly**<br /><br /> **Vlákno** - určuje funkce řízení sběru dat na úrovni vlákna. Profilování je spuštěno nebo zastaveno pouze pro aktuální vlákno. Stav profilování jiných vláken není ovlivněn. Výchozí hodnota je podproces.<br /><br /> **Proces** - určuje funkce řízení shromažďování dat profilování na úrovni procesu. Profilování se spustí nebo zastaví pro všechna vlákna v aktuálním procesu. Stav profilování jiných procesů není ovlivněn.<br /><br /> **Globální** - určuje globální (meziprocesové) funkce řízení sběru dat.<br /><br /> Pokud nezadáte úroveň profilování, dojde k chybě.|
|**Začít** `:{` **uvnitř** `&#124;` **venku**`},funcname`|Omezuje shromažďování dat na cílovou funkci a podřízené funkce volané tímto úkolem.<br /><br /> **Uvnitř** - Vloží funkci StartProfile bezprostředně za zadání do cílové funkce. Vloží funkci StopProfile bezprostředně před každou vrácenou funkci v cílové funkci.<br /><br /> **Venku** - Vloží funkci StartProfile bezprostředně před každé volání cílové funkce. Vloží funkci StopProfile ihned po každém volání cílové funkce.<br /><br /> `funcname`- název cílové funkce.|
|**Pozastavit** `:{` **uvnitř** `&#124;` **vně**`},funcname`|Vyloučí shromažďování dat pro cílovou funkci a podřízené funkce volané funkcí.<br /><br /> **Uvnitř** - Vloží funkci SuspendProfile bezprostředně za zadání do cílové funkce. Vloží funkci ResumeProfile bezprostředně před každou vrácenou funkci v cílové funkci.<br /><br /> **Venku** - Vloží funkci SuspendProfile bezprostředně před zadání cílové funkce. Vloží funkci ResumeProfile bezprostředně za ukončení cílové funkce.<br /><br /> `funcname`- název cílové funkce.<br /><br /> Pokud cílová funkce obsahuje funkci StartProfile, vloží se před ni funkce SuspendProfile. Pokud cílová funkce obsahuje funkci StopProfile, funkce ResumeProfile se za ní vloží.|
|**StartOnly:** `{` **Před po** `&#124;` **After** `&#124;` **horním** `&#124;` **dně**`},funcname`|Zahájí shromažďování dat během spuštění profilování. Vloží funkci Rozhraní API StartProfile do zadaného umístění.<br /><br /> **Před** - bezprostředně před zadáním cílové funkce.<br /><br /> **Po** - bezprostředně po ukončení cílové funkce.<br /><br /> **Nahoru** - bezprostředně po zadání cílové funkce.<br /><br /> **Dole** - bezprostředně před každým návratem v cílové funkci.<br /><br /> `funcname`- název cílové funkce.|
|**StopOnly:**{**Před**`&#124;`**po**`&#124;`**horním**`&#124;`**dně**}`,funcname`|Zastaví shromažďování dat během spuštění profilování. Vloží funkci StopProfile do zadaného umístění.<br /><br /> **Před** - bezprostředně před zadáním cílové funkce.<br /><br /> **Po** - bezprostředně po ukončení cílové funkce.<br /><br /> **Nahoru** - bezprostředně po zadání cílové funkce.<br /><br /> **Dole** - bezprostředně před každým návratem v cílové funkci.<br /><br /> `funcname`- název cílové funkce.|
|**Pouze pozastavit:**{**před**`&#124;`**po**`&#124;`**horním**`&#124;`**dně**}`,funcname`|Zastaví shromažďování dat během spuštění profilování. Vloží rozhraní API profilu/suspendprofile do zadaného umístění.<br /><br /> **Před** - bezprostředně před zadáním cílové funkce.<br /><br /> **Po** - bezprostředně po ukončení cílové funkce.<br /><br /> **Nahoru** - bezprostředně po zadání cílové funkce.<br /><br /> **Dole** - bezprostředně před každým návratem v cílové funkci.<br /><br /> `funcname`- název cílové funkce.<br /><br /> Pokud cílová funkce obsahuje funkci StartProfile, vloží se před ni funkce SuspendProfile.|
|**ResumeOnly:**{**Před**`&#124;`**Po**`&#124;`**horním**`&#124;`**dně**}`,funcname`|Zahájí nebo obnoví shromažďování dat během profilování spustit.<br /><br /> Obvykle se používá ke spuštění profilování po **suspendonly** možnost přestalprofilování. Vloží rozhraní REResumeProfile API v zadaném umístění.<br /><br /> **Před** - bezprostředně před zadáním cílové funkce.<br /><br /> **Po** - bezprostředně po ukončení cílové funkce.<br /><br /> **Nahoru** - bezprostředně po zadání cílové funkce.<br /><br /> **Dole** - bezprostředně před každým návratem v cílové funkci.<br /><br /> `funcname`- název cílové funkce.<br /><br /> Pokud cílová funkce obsahuje funkci StopProfile, funkce ResumeProfile se za ní vloží.|

## <a name="see-also"></a>Viz také
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [VSInstr varování](../profiling/vsinstr-warnings.md)
- [Zobrazení sestavy výkonu](../profiling/performance-report-views.md)
