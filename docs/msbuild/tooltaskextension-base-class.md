---
title: Základní třída ToolTaskExtension – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9aa052a0fd2216d5f3d85e99794d9ac883a09e2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631689"
---
# <a name="tooltaskextension-base-class"></a>ToolTaskExtension – základní třída

Mnoho úloh dědí z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy, která dědí z třídy <xref:Microsoft.Build.Utilities.ToolTask> , která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Tento řetěz dědičnosti přidá několik parametrů k úlohám, které jsou z nich odvozeny. Tyto parametry jsou uvedeny v tomto dokumentu.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry základních tříd.

| Parametr | Popis |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | Volitelný <xref:Microsoft.Build.Framework.IBuildEngine> parametr.<br /><br /> Určuje rozhraní Build Engine dostupné pro úlohy. Modul sestavení automaticky nastaví tento parametr tak, aby umožňoval úkolům volat zpět do něj. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | Volitelný <xref:Microsoft.Build.Framework.IBuildEngine2> parametr.<br /><br /> Určuje rozhraní Build Engine dostupné pro úlohy. Modul sestavení automaticky nastaví tento parametr tak, aby umožňoval úkolům volat zpět do něj.<br /><br /> Toto je vlastnost pohodlí, aby autoři úloh, které dědí z této třídy, nemuseli přetypovat hodnotu z `IBuildEngine` na `IBuildEngine2` . |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | Volitelný <xref:Microsoft.Build.Framework.IBuildEngine3> parametr.<br /><br /> Určuje rozhraní modulu sestavení poskytované hostitelem. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Volitelný `bool` parametr.<br /><br /> Když je `true` Tato úloha nastavena na, projde tento úkol **/q** do *cmd.exe* příkazového řádku, aby se příkazový řádek nezkopíroval do STDOUT. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Volitelný `String` parametr pole.<br /><br /> Pole párů proměnných prostředí oddělené znaménkem rovná se. Tyto proměnné jsou předány do vytvořeného spustitelného souboru v kombinaci s běžným nebo selektivním přepsáním normálního bloku prostředí. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Volitelný `Int32` výstup – parametr jen pro čtení.<br /><br /> Určuje ukončovací kód, který je poskytnut spuštěným příkazem. Pokud úloha nahlásila chyby, ale proces měl ukončovací kód 0 (úspěch), je nastaven na hodnotu-1. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | Volitelný <xref:Microsoft.Build.Framework.ITaskHost> parametr.<br /><br /> Určuje instanci objektu hostitele (může mít hodnotu null). Modul sestavení nastavuje tuto vlastnost, pokud má rozhraní IDE hostitele přidružený objekt hostitele s touto konkrétní úlohou. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | Volitelný <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametr jen pro čtení.<br /><br /> Načte instanci <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> třídy, která obsahuje metody protokolování úkolů. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | `bool`Parametr možnosti.<br /><br /> Pokud `true` jsou všechny zprávy přijaté ve standardním datovém proudu chyb protokolovány jako chyby. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Volitelný `String` parametr.<br /><br /> Důležitost, se kterou chcete protokolovat text z standardního výstupního proudu. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Volitelný `String` parametr.<br /><br /> Důležitost, se kterou chcete protokolovat text z standardního výstupního proudu. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Virtuální volitelný `Int32` parametr.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je ukončen spustitelný soubor úlohy. Výchozí hodnota je `Int.MaxValue` , což značí, že není k dispozici žádný časový interval. Časový limit je v milisekundách. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Virtuální volitelný `string` parametr.<br /><br /> Projekty mohou tuto implementaci implementovat pro přepsání nástroje. Úkoly mohou tuto potlačit, aby zachovaly nástroj. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Volitelný `string` parametr.<br /><br /> Určuje umístění, ze kterého úloha načte základní spustitelný soubor. Pokud tento parametr není zadán, úloha použije cestu instalace sady SDK, která odpovídá verzi rozhraní .NET Framework, která spouští nástroj MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Volitelný `bool` parametr.<br /><br /> Když `true` je tato úloha nastavená na, vytvoří dávkový soubor pro příkazový řádek a provede ho pomocí příkazového procesoru namísto provedení příkazu přímo. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Volitelný `bool` parametr.<br /><br /> Když `true` je tato úloha nastavena na, vydává tento úkol uzel při provádění jeho úkolu. |

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
