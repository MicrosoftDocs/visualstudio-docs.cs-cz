---
title: Třída TaskScheduler – vnitřní členy | Microsoft Docs
description: Seznamte se s interními členy třídy System.Threading.Tasks.TaskScheduler, které vám pomůžou implementovat vlastní ladicí program.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58b370a6742387f7493e4c6357cffd05f2bd88a5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900145"
---
# <a name="taskscheduler-class---internal-members"></a>Třída TaskScheduler – interní členy
Tento článek popisuje interní členy <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> třídy, které vám pomohou implementovat vlastní ladicí program. Obecné informace o této třídě najdete v <xref:System.Threading.Tasks.TaskScheduler> referenčním článku.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že nemůžete přistupovat k těmto interním členům z .NET Framework, je následující syntaxe k dispozici v souboru Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|Název|Description|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Načte pole všech naplánovaných úloh.|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Načte pole všech objektů, <xref:System.Threading.Tasks.TaskScheduler> které jsou aktuálně aktivní.|

## <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Interní informace o paralelním rozšíření pro .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
