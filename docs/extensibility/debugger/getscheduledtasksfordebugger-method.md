---
title: Metoda GetScheduledTasksForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fca6c8e92cd0b4755bd79b8e142a7e1d283f868d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738659"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger – metoda
Načte pole všech naplánovaných úloh.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členovi z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Návratová hodnota
 Pole všech naplánovaných úloh. Jednotlivé úlohy se spouštějí nebo se dokončily.

## <a name="remarks"></a>Poznámky
 Tato metoda není bezpečná pro přístup z více vláken a neměli byste ji používat souběžně s jinými instancemi <xref:System.Threading.Tasks.TaskScheduler> . Tuto metodu zavolejte z ladicího programu pouze v případě, že ladicí program pozastavil všechna ostatní vlákna.

## <a name="see-also"></a>Viz také
- [TaskScheduler – třída](../../extensibility/debugger/taskscheduler-class-internal-members.md)
