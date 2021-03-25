---
description: Načte pole všech objektů System. Threading. Tasks. TaskScheduler, které jsou aktuálně aktivní.
title: Metoda GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d024e44dee8e7513d862e3d299c2ed2b9e53cd5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054852"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger – metoda
Načte pole všech <xref:System.Threading.Tasks.TaskScheduler> objektů, které jsou aktuálně aktivní.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členovi z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Vrácená hodnota
 Pole všech <xref:System.Threading.Tasks.TaskScheduler> objektů, které jsou v tuto chvíli aktivní <xref:System.AppDomain> .

## <a name="remarks"></a>Poznámky
 Tato metoda není bezpečná pro přístup z více vláken a neměli byste ji používat souběžně s jinými instancemi <xref:System.Threading.Tasks.TaskScheduler> . Tuto metodu zavolejte z ladicího programu pouze v případě, že ladicí program pozastavil všechna ostatní vlákna.

## <a name="see-also"></a>Viz také
- [TaskScheduler – třída](../../extensibility/debugger/taskscheduler-class-internal-members.md)
