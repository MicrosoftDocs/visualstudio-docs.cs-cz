---
description: Úkol dokončil provádění delegáta a implicitně čeká na dokončení připojených podřízených úloh.
title: TASK_STATE_WAITING_ON_CHILDREN pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b795a20ba19b1309b3f3bf972beed70549d72d88
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900158"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN pole
Úkol dokončil provádění delegáta a implicitně čeká na dokončení připojených podřízených úloh.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členovi z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Poznámky
 Pokud pole [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) obsahuje tuto hodnotu, <xref:System.Threading.Tasks.Task.Status%2A> vlastnost vrátí hodnotu <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Viz také
- [Task – třída](../../extensibility/debugger/task-class-internal-members.md)
