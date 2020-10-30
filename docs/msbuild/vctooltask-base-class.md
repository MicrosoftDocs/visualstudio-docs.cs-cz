---
title: Třída VCToolTask | Microsoft Docs
description: Přečtěte si o několika parametrech, které třída Base VCToolTask přidá do úkolů, které z ní dědí.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b2e45d7c672ebc2177c2bb197399133e7b077a5c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046737"
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
|**GenerateCommandLineExceptSwitches**|Volitelný **řetězcový** parametr.<br/><br/>Používá řetězec Values **[]** *switchesToRemove* , **CommandLineFormat** *Format* [default = CommandLineFormat. ForBuildLog] a **EscapeFormat** *EscapeFormat* [default = EscapeFormat. default].|

## <a name="see-also"></a>Viz také

[Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)<br/>
[Úlohy](../msbuild/msbuild-tasks.md)
