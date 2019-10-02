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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7734f852da997836cf2f42fd3f6b96e9decdf8dd
ms.sourcegitcommit: 628eb202a1153ebfe69c668f966f821b98b34b34
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71720560"
---
# <a name="tooltaskextension-base-class"></a>Základní třída ToolTaskExtension –
Mnoho úloh dědí z třídy <xref:Microsoft.Build.Tasks.ToolTaskExtension>, která dědí z třídy <xref:Microsoft.Build.Utilities.ToolTask>, která sama dědí z třídy <xref:Microsoft.Build.Utilities.Task>. Tento řetěz dědičnosti přidá několik parametrů k úlohám, které jsou z nich odvozeny. Tyto parametry jsou uvedeny v tomto dokumentu.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry základních tříd.

| Parametr | Popis |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | Volitelný <xref:Microsoft.Build.Framework.IBuildEngine> parametr.<br /><br /> Určuje rozhraní Build Engine dostupné pro úlohy. Modul sestavení automaticky nastaví tento parametr tak, aby umožňoval úkolům volat zpět do něj. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | Volitelný <xref:Microsoft.Build.Framework.IBuildEngine2> parametr.<br /><br /> Určuje rozhraní Build Engine dostupné pro úlohy. Modul sestavení automaticky nastaví tento parametr tak, aby umožňoval úkolům volat zpět do něj.<br /><br /> Toto je vlastnost pohodlí, aby autoři úloh, které dědí z této třídy, nemuseli přetypovat hodnotu z `IBuildEngine` na `IBuildEngine2`. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | Volitelný <xref:Microsoft.Build.Framework.IBuildEngine3> parametr.<br /><br /> Určuje rozhraní modulu sestavení poskytované hostitelem. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Volitelný `bool` parametr.<br /><br /> Pokud je nastavena hodnota `true`, projde Tato úloha **/q** do příkazového řádku *cmd. exe* , aby se příkazový řádek nezkopíroval do STDOUT. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Volitelný parametr `String`.<br /><br /> Pole párů proměnných prostředí oddělené znaménkem rovná se. Tyto proměnné jsou předány do vytvořeného spustitelného souboru v kombinaci s běžným nebo selektivním přepsáním normálního bloku prostředí. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Volitelná hodnota `Int32` výstupního parametru jen pro čtení.<br /><br /> Určuje ukončovací kód, který je poskytnut spuštěným příkazem. Pokud úloha nahlásila chyby, ale proces měl ukončovací kód 0 (úspěch), je nastaven na hodnotu-1. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | Volitelný <xref:Microsoft.Build.Framework.ITaskHost> parametr.<br /><br /> Určuje instanci objektu hostitele (může mít hodnotu null). Modul sestavení nastavuje tuto vlastnost, pokud má rozhraní IDE hostitele přidružený objekt hostitele s touto konkrétní úlohou. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | Volitelná hodnota <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametru jen pro čtení.<br /><br /> Načte instanci třídy <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension>, která obsahuje metody protokolování úkolů. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Možnost @no__t parametr-0<br /><br /> Pokud `true`, všechny zprávy přijaté do standardního chybového datového proudu jsou protokolovány jako chyby. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Volitelný `String` parametr.<br /><br /> Důležitost, se kterou chcete protokolovat text z standardního výstupního proudu. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Volitelný `String` parametr.<br /><br /> Důležitost, se kterou chcete protokolovat text z standardního výstupního proudu. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Virtuální volitelný parametr `Int32`.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je ukončen spustitelný soubor úlohy. Výchozí hodnota je `Int.MaxValue`, což značí, že není k dispozici žádný časový interval. Časový limit je v milisekundách. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Virtuální volitelný parametr `string`.<br /><br /> Projekty mohou tuto implementaci implementovat pro přepsání nástroje. Úkoly mohou tuto potlačit, aby zachovaly nástroj. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Volitelný `string` parametr.<br /><br /> Určuje umístění, ze kterého úloha načte základní spustitelný soubor. Pokud tento parametr není zadán, úloha použije cestu instalace sady SDK, která odpovídá verzi rozhraní, na které běží [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Volitelný `bool` parametr.<br /><br /> Když se nastaví na `true`, tato úloha vytvoří dávkový soubor pro příkazový řádek a provede ho pomocí příkazového procesoru namísto provedení příkazu přímo. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Volitelný `bool` parametr.<br /><br /> Když je nastavená hodnota `true`, tento úkol při provádění jeho úlohy vydává uzel. |

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úkoly](../msbuild/msbuild-tasks.md)