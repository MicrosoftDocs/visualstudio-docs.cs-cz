---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 40108f56ee9d64688fc665fdef0e0ab731bddfff
ms.sourcegitcommit: 596f92fcc84e6f4494178863a66aed85afe0bb08
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82204617"
---
### <a name="tooltaskextension-parameters"></a>Parametry ToolTaskExtension –

Tato úloha dědí z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy, která dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Tento řetěz dědičnosti přidá několik parametrů k úlohám, které jsou z nich odvozeny.

Následující tabulka popisuje parametry základních tříd:

| Parametr | Popis |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Volitelný `bool` parametr.<br /><br /> Při nastavení na `true`tento úkol projde příkazem **/q** do příkazového řádku *cmd. exe* , aby se příkazový řádek nezkopíroval do STDOUT. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Volitelný `String` parametr pole.<br /><br /> Pole párů proměnných prostředí oddělené znaménkem rovná se. Tyto proměnné jsou předány do vytvořeného spustitelného souboru v kombinaci s běžným nebo selektivním přepsáním normálního bloku prostředí. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Volitelný `Int32` výstup – parametr jen pro čtení.<br /><br /> Určuje ukončovací kód, který je poskytnut spuštěným příkazem. Pokud úloha nahlásila chyby, ale proces měl ukončovací kód 0 (úspěch), je nastaven na hodnotu-1. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Parametr `bool` možnosti.<br /><br /> Pokud `true`jsou všechny zprávy přijaté ve standardním datovém proudu chyb protokolovány jako chyby. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Volitelný `bool` parametr.<br /><br /> Pokud `true`jsou všechny zprávy přijaté ve standardním datovém proudu chyb protokolovány jako chyby. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Volitelný `String` parametr.<br /><br /> Důležitost, se kterou chcete protokolovat text z standardního výstupního proudu. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Volitelný `String` parametr.<br /><br /> Důležitost, se kterou chcete protokolovat text z standardního výstupního proudu. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Volitelný `Int32` parametr.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je ukončen spustitelný soubor úlohy. Výchozí hodnota je `Int.MaxValue`, což značí, že není k dispozici žádný časový interval. Časový limit je v milisekundách. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Volitelný `string` parametr.<br /><br /> Projekty mohou tuto implementaci implementovat pro přepsání nástroje. Úkoly mohou tuto potlačit, aby zachovaly nástroj. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Volitelný `string` parametr.<br /><br /> Určuje umístění, ze kterého úloha načte základní spustitelný soubor. Pokud tento parametr není zadán, úloha použije cestu instalace sady SDK, která odpovídá verzi rozhraní .NET Framework, která spouští nástroj MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Volitelný `bool` parametr.<br /><br /> Když je tato `true`úloha nastavená na, vytvoří dávkový soubor pro příkazový řádek a provede ho pomocí příkazového procesoru namísto provedení příkazu přímo. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Volitelný `bool` parametr.<br /><br /> Když je tato `true`úloha nastavena na, vydává tento úkol uzel při provádění jeho úkolu. |
