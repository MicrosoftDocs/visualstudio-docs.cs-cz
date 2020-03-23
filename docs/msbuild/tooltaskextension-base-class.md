---
title: Základní třída rozšíření ToolTaskExtension | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631689"
---
# <a name="tooltaskextension-base-class"></a>Základní třída ToolTaskExtension

Mnoho úkolů dědí z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy, <xref:Microsoft.Build.Utilities.ToolTask> která dědí z <xref:Microsoft.Build.Utilities.Task> třídy, která sama dědí z třídy. Tento řetězec dědičnosti přidá několik parametrů k úkolům, které z nich vyplývají. Tyto parametry jsou uvedeny v tomto dokumentu.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry základních tříd.

| Parametr | Popis |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | Volitelný <xref:Microsoft.Build.Framework.IBuildEngine> parametr.<br /><br /> Určuje rozhraní modulu sestavení, které je k dispozici pro úkoly. Modul sestavení automaticky nastaví tento parametr tak, aby úkoly volat zpět do něj. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | Volitelný <xref:Microsoft.Build.Framework.IBuildEngine2> parametr.<br /><br /> Určuje rozhraní modulu sestavení, které je k dispozici pro úkoly. Modul sestavení automaticky nastaví tento parametr tak, aby úkoly volat zpět do něj.<br /><br /> Toto je vlastnost pohodlí tak, aby autoři úloh dědí z `IBuildEngine` `IBuildEngine2`této třídy nemusí přetypovat hodnotu z do . |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | Volitelný <xref:Microsoft.Build.Framework.IBuildEngine3> parametr.<br /><br /> Určuje rozhraní modulu sestavení poskytované hostitelem. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Volitelný `bool` parametr.<br /><br /> Je-li `true`nastavena na , předá tato **úloha /Q** příkazovému řádku *cmd.exe* tak, aby se příkazový řádek nezkopíroval do stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Volitelný `String` parametr pole.<br /><br /> Pole párů proměnných prostředí, oddělených rovnítky. Tyto proměnné jsou předány zplodil spustitelný soubor kromě nebo selektivně přepsání, pravidelné blok prostředí. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Volitelný `Int32` výstupní parametr jen pro čtení.<br /><br /> Určuje ukončovací kód, který je k dispozici provedeným příkazem. Pokud úloha zaznamenala všechny chyby, ale proces měl ukončovací kód 0 (úspěch), je tato možnost nastavena na -1. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | Volitelný <xref:Microsoft.Build.Framework.ITaskHost> parametr.<br /><br /> Určuje instanci objektu hostitele (může mít hodnotu null). Modul sestavení nastaví tuto vlastnost, pokud ide hostitele přidruží objekt hostitele k této konkrétní úloze. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | Volitelný <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametr jen pro čtení.<br /><br /> Získá instanci <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> třídy, která obsahuje metody protokolování úloh. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Parametr `bool` možnosti.<br /><br /> Pokud `true`jsou všechny zprávy přijaté ve standardním datovém proudu chyb zaznamenány jako chyby. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Volitelný `String` parametr.<br /><br /> Důležitost, s níž chcete protokolovat text ze standardního datového proudu. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Volitelný `String` parametr.<br /><br /> Důležitost, s níž chcete protokolovat text ze standardního datového proudu. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Virtuální `Int32` volitelný parametr.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je spustitelný soubor úlohy ukončen. Výchozí hodnota `Int.MaxValue`je , označující, že neexistuje žádné časové období. Časový rozsah je v milisekundách. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Virtuální `string` volitelný parametr.<br /><br /> Projekty mohou implementovat to přepsat ToolName. Úkoly mohou přepsat to zachovat ToolName. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Volitelný `string` parametr.<br /><br /> Určuje umístění, ze kterého úloha načte základní spustitelný soubor. Pokud tento parametr není zadán, úloha používá instalační cestu sady SDK, která odpovídá verzi rozhraní, která je spuštěna MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Volitelný `bool` parametr.<br /><br /> Pokud je `true`tato úloha nastavena na , vytvoří dávkový soubor pro příkazový řádek a provede jej pomocí příkazového procesoru namísto přímého spuštění příkazu. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Volitelný `bool` parametr.<br /><br /> Pokud je `true`nastavena na , tento úkol dává uzel při provádění jeho úlohy. |

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
