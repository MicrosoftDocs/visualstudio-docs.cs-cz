---
title: m_stateFlags pole | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b504d134c8951072795dc2e202cf05082b12cb64
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738387"
---
# <a name="m_stateflags-field"></a>m_stateFlags pole
Ukládá informace o aktuálním <xref:System.Threading.Tasks.Task> stavu objektu.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestava:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že k tomuto internímu členu nemáte přístup z rozhraní .NET Framework, je ve společném zprostředkujícím jazyce (CIL) k dispozici následující syntaxe.

## <a name="syntax"></a>Syntaxe

```csharp
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags
```

## <a name="remarks"></a>Poznámky
 Obvykle používáte <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> vlastnost pro přístup k této hodnotě.

 Tento člen může být libovolná kombinace následujících hodnot:

- [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)

- [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)

- [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)

- [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)

- [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)

## <a name="see-also"></a>Viz také
- [Třída úkolu](../../extensibility/debugger/task-class-internal-members.md)
