---
title: Třída VCToolTask | Dokumenty společnosti Microsoft
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: df75bb998d2b8c6486e20c4c3ca0d80347c8f88a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591668"
---
# <a name="vctooltask-base-class"></a>Základní třída VCToolTask

Mnoho úkolů nakonec dědí z třídy <xref:Microsoft.Build.Utilities.Task> a [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) třídy. Tato třída přidá několik parametrů k úkolům, které z nich vyplývají. Tyto parametry jsou uvedeny v tomto dokumentu.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry základní třídy **VCToolTask.**

|Parametr|Popis|
|---------------|-----------------|
|**Hodnoty ActiveToolSwitches**|Volitelný **řetězec\<slovníku, parametr ToolSwitch>.**|
|**Další možnosti**|Volitelný parametr **řetězce.**|
|**EfektivníWorkingDirectory**|Volitelný parametr **řetězce.**|
|**EnableErrorListRegex**|Volitelný **parametr bool.**<br/><br/>Výchozí je `true`.|
|**ErrorListRegex**|Volitelný parametr **ITaskItem[].**|
|**Vyloučení seznamu errorlist**|Volitelný parametr **ITaskItem[].**|
|**GenerateCommandLine**|Volitelný parametr **řetězce.**<br/><br/>Používá hodnoty **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] a **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Volitelný parametr **řetězce.**<br/><br/>Používá řetězce **hodnot[]** *switchesToRemove*, **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] a **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|

## <a name="see-also"></a>Viz také

[Odkaz na úkol](../msbuild/msbuild-task-reference.md)<br/>
[Úlohy](../msbuild/msbuild-tasks.md)
