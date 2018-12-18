---
title: Tooltaskextension – základní třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8856011e8b85f049c53947a785f1479e1db25368
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888551"
---
# <a name="tooltaskextension-base-class"></a>Tooltaskextension – základní třída
Dědí celou řadu úloh <xref:Microsoft.Build.Tasks.ToolTaskExtension> třída, která dědí z <xref:Microsoft.Build.Utilities.ToolTask> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Tento řetězec dědičnosti přidá několik parametrů do úlohy, které jsou odvozeny z nich. Tyto parametry jsou uvedeny v tomto dokumentu.  

## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry základní třídy.  


| Parametr | Popis |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | Volitelné <xref:Microsoft.Build.Framework.IBuildEngine> parametru.<br /><br /> Určuje rozhraní modul sestavení k dispozici pro úlohy. Stroj sestavení automaticky nastaví tento parametr umožnit, aby zpětné volání do ní úlohy. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | Volitelné <xref:Microsoft.Build.Framework.IBuildEngine2> parametru.<br /><br /> Určuje rozhraní modul sestavení k dispozici pro úlohy. Stroj sestavení automaticky nastaví tento parametr umožnit, aby zpětné volání do ní úlohy.<br /><br /> Toto je vlastnost pohodlí, takže autoři úloh dědění z této třídy nemají k přetypování hodnoty z `IBuildEngine` k `IBuildEngine2`. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | Volitelné <xref:Microsoft.Build.Framework.IBuildEngine3> parametru.<br /><br /> Určuje rozhraní modul sestavení poskytovány tímto hostitelem. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Volitelné `bool` parametru.<br /><br /> Při nastavení na `true`, tato úloha předá **/Q** k *cmd.exe* příkazový řádek tak, že příkazový řádek není se zkopíruje do stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Volitelné `String` parametr pole.<br /><br /> Pole párů proměnné prostředí oddělené rovnítko. Tyto proměnné jsou předány do nové kopie spustitelný soubor kromě nebo selektivní přepsání blok regulární prostředí. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Volitelné `Int32` výstupní parametr jen pro čtení.<br /><br /> Určuje ukončovací kód, který je poskytován provedeného příkazu. Pokud úloha protokoluje chyby, ale proces má ukončovací kód 0 (úspěch), to je nastavena na hodnotu -1. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | Volitelné <xref:Microsoft.Build.Framework.ITaskHost> parametru.<br /><br /> Určuje instanci objektu hostitele (může mít hodnotu null). Stroj sestavení nastaví tuto vlastnost, pokud hostitel integrovaného vývojového prostředí přidružené k objekt hostitele tuto konkrétní úlohu. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | Volitelné <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametr jen pro čtení.<br /><br /> Získá instanci objektu <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> třídu, která obsahuje metody protokolování úloh. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Možnost `bool` parametru.<br /><br /> Pokud `true`, všechny zprávy přijaté ve standardní chybový proud přihlášeni jako chyby. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Volitelné `String` parametru.<br /><br /> Význam, pomocí kterého se má text protokolu úroveň ze standard na datový proud. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Volitelné `String` parametru.<br /><br /> Význam, pomocí kterého se má text protokolu úroveň ze standard na datový proud. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Virtuální volitelné `Int32` parametru.<br /><br /> Určuje množství času, v milisekundách, po jejichž uplynutí je spustitelný soubor s úkolem ukončen. Výchozí hodnota je `Int.MaxValue`, která udává, že neexistuje žádný časový limit. Časový limit je uvedena v milisekundách. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Virtuální volitelné `string` parametru.<br /><br /> Projekty mohou implementovat toto přepsání název nástroje. Úkoly mohou přepsat tuto hodnotu na zachovat název nástroje. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Volitelné `string` parametru.<br /><br /> Určuje umístění, kde úloha načítá základní spustitelný soubor. Pokud není tento parametr zadán, použije úloha instalační cestu sady SDK, která odpovídá verzi rozhraní framework, na kterém běží [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Volitelné `bool` parametru.<br /><br /> Pokud je nastavena na `true`, tato úloha vytvoří dávkový soubor pro příkazový řádek a spustí pomocí procesor příkazu namísto provádění příkazu přímo. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Volitelné `bool` parametru.<br /><br /> Pokud je nastavena na `true`, tato úloha provede uzlu při provádění svých úloh. |

## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)