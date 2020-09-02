---
title: Třída VCToolTask | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591668"
---
# <a name="vctooltask-base-class"></a>VCToolTask – základní třída

Mnohé úlohy jsou nakonec děděny ze třídy <xref:Microsoft.Build.Utilities.Task> a třídy [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) . Tato třída přidá několik parametrů do úkolů, které jsou z nich odvozeny. Tyto parametry jsou uvedeny v tomto dokumentu.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry základní třídy **VCToolTask** .

|Parametr|Popis|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Volitelný **parametr \<string, ToolSwitch> slovníku** .|
|**AdditionalOptions**|Volitelný **řetězcový** parametr.|
|**EffectiveWorkingDirectory**|Volitelný **řetězcový** parametr.|
|**EnableErrorListRegex**|Volitelný parametr **bool** .<br/><br/>Výchozí je `true`.|
|**ErrorListRegex**|Volitelný parametr **ITaskItem []** .|
|**ErrorListListExclusion**|Volitelný parametr **ITaskItem []** .|
|**GenerateCommandLine**|Volitelný **řetězcový** parametr.<br/><br/>Používá hodnoty **CommandLineFormat** *Format* [default = CommandLineFormat. ForBuildLog] a **EscapeFormat** *EscapeFormat* [default = EscapeFormat. default].|
|**GenerateCommandLineExceptSwitches**|Volitelný **řetězcový** parametr.<br/><br/>Používá řetězec Values **[]** *switchesToRemove*, **CommandLineFormat** *Format* [default = CommandLineFormat. ForBuildLog] a **EscapeFormat** *EscapeFormat* [default = EscapeFormat. default].|

## <a name="see-also"></a>Viz také

[Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)<br/>
[Úlohy](../msbuild/msbuild-tasks.md)
