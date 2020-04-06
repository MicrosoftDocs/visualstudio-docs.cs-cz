---
title: Metoda GetTaskSchedulersForDebugger | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3b0c8c16b10a4cf2268161d8a2db96c10303b1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738644"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger – metoda
Načte pole všech <xref:System.Threading.Tasks.TaskScheduler> objektů, které jsou aktuálně aktivní.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestava:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že k tomuto internímu členu nemáte přístup z rozhraní .NET Framework, je ve společném zprostředkujícím jazyce (CIL) k dispozici následující syntaxe.

## <a name="syntax"></a>Syntaxe

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Návratová hodnota
 Pole všech <xref:System.Threading.Tasks.TaskScheduler> objektů, které jsou aktuálně <xref:System.AppDomain>aktivní v tomto .

## <a name="remarks"></a>Poznámky
 Tato metoda není bezpečná pro přístup z více vláken a <xref:System.Threading.Tasks.TaskScheduler>neměli byste ji používat souběžně s jinými instancemi rozhraní . Volání této metody z ladicího programu pouze v případě, že ladicí program pozastavil všechna ostatní vlákna.

## <a name="see-also"></a>Viz také
- [Třída TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
