---
title: TASK_STATE_WAITING_ON_CHILDREN pole | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27b9963db54d939b3d509da451478c20dbe0e7d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712588"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN pole
Úloha byla dokončena při provádění svého delegáta a implicitně čeká na dokončení připojených podřízených úloh.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestava:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že k tomuto internímu členu nemáte přístup z rozhraní .NET Framework, je ve společném zprostředkujícím jazyce (CIL) k dispozici následující syntaxe.

## <a name="syntax"></a>Syntaxe

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Poznámky
 Pokud [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) pole obsahuje tuto <xref:System.Threading.Tasks.Task.Status%2A> hodnotu, vrátí vlastnost <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.

## <a name="see-also"></a>Viz také
- [Třída úkolu](../../extensibility/debugger/task-class-internal-members.md)
