---
description: Načte pole všech objektů System.Threading.Tasks.TaskScheduler, které jsou aktuálně aktivní.
title: GetTaskSchedulersForDebugger – metoda | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58cb913f5dbc729c297de8a34aa5dd4c3c99b48a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900912"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger – metoda
Načte pole všech objektů, <xref:System.Threading.Tasks.TaskScheduler> které jsou aktuálně aktivní.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členu z .NET Framework, je následující syntaxe k dispozici v souboru Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Vrácená hodnota
 Pole všech <xref:System.Threading.Tasks.TaskScheduler> objektů, které jsou aktuálně aktivní v tomto objektu <xref:System.AppDomain> .

## <a name="remarks"></a>Poznámky
 Tato metoda není bezpečná pro přístup z více vláken a neměla by se používat souběžně s jinými instancemi <xref:System.Threading.Tasks.TaskScheduler> . Tuto metodu volejte z ladicího programu pouze v případě, že ladicí program pozastavil všechna ostatní vlákna.

## <a name="see-also"></a>Viz také
- [TaskScheduler – třída](../../extensibility/debugger/taskscheduler-class-internal-members.md)
