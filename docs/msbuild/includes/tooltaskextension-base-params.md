---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 6fd0fc6fd4f2e54c0d15f649139b649797f8336f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89043071"
---
### <a name="tooltaskextension-parameters"></a>Parametry ToolTaskExtension –

Tato úloha dědí z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy, která dědí z třídy <xref:Microsoft.Build.Utilities.ToolTask> , která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Tento řetěz dědičnosti přidá několik parametrů k úlohám, které jsou z nich odvozeny.

Následující tabulka popisuje parametry základních tříd:

| Parametr | Popis |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Volitelný `bool` parametr.<br /><br /> Když je `true` Tato úloha nastavena na, projde tento úkol **/q** do *cmd.exe* příkazového řádku, aby se příkazový řádek nezkopíroval do STDOUT. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Volitelný `String` parametr pole.<br /><br /> Pole definic proměnných prostředí, které jsou odděleny středníky. Každá definice by měla určovat název a hodnotu proměnné prostředí oddělené symbolem rovná se. Tyto proměnné jsou předány do vytvořeného spustitelného souboru v kombinaci s běžným nebo selektivním přepsáním normálního bloku prostředí. Například, `Variable1=Value1;Variable2=Value2`. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Volitelný `Int32` výstup – parametr jen pro čtení.<br /><br /> Určuje ukončovací kód, který je poskytnut spuštěným příkazem. Pokud úloha nahlásila chyby, ale proces měl ukončovací kód 0 (úspěch), je nastaven na hodnotu-1. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | `bool`Parametr možnosti.<br /><br /> Pokud `true` jsou všechny zprávy přijaté ve standardním datovém proudu chyb protokolovány jako chyby. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Volitelný `bool` parametr.<br /><br /> Pokud `true` jsou všechny zprávy přijaté ve standardním datovém proudu chyb protokolovány jako chyby. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Volitelný `String` parametr.<br /><br /> Důležitost, se kterou chcete protokolovat text z standardního výstupního proudu. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Volitelný `String` parametr.<br /><br /> Důležitost, se kterou chcete protokolovat text z standardního výstupního proudu. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Volitelný `Int32` parametr.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je ukončen spustitelný soubor úlohy. Výchozí hodnota je `Int.MaxValue` , což značí, že není k dispozici žádný časový interval. Časový limit je v milisekundách. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Volitelný `string` parametr.<br /><br /> Projekty mohou tuto implementaci implementovat pro přepsání nástroje. Úkoly mohou tuto potlačit, aby zachovaly nástroj. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Volitelný `string` parametr.<br /><br /> Určuje umístění, ze kterého úloha načte základní spustitelný soubor. Pokud tento parametr není zadán, úloha použije cestu instalace sady SDK, která odpovídá verzi rozhraní .NET Framework, která spouští nástroj MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Volitelný `bool` parametr.<br /><br /> Když `true` je tato úloha nastavená na, vytvoří dávkový soubor pro příkazový řádek a provede ho pomocí příkazového procesoru namísto provedení příkazu přímo. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Volitelný `bool` parametr.<br /><br /> Když `true` je tato úloha nastavena na, vydává tento úkol uzel při provádění jeho úkolu. |
