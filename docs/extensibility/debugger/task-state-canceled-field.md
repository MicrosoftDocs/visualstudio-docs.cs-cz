---
title: TASK_STATE_CANCELED pole | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d59335a418febef45ebe35d4590c72b486921639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712749"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED pole
Úloha byla zrušena před dosažením stavu spuštění nebo její zrušení bylo dokončeno bez výjimky.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestava:** mscorlib (v mscorlib.dll)

 Vzhledem k tomu, že k tomuto internímu členu nemáte přístup z rozhraní .NET Framework, je ve společném zprostředkujícím jazyce (CIL) k dispozici následující syntaxe.

## <a name="syntax"></a>Syntaxe

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Poznámky
 Pokud [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) pole obsahuje tuto <xref:System.Threading.Tasks.Task.Status%2A> hodnotu, vrátí vlastnost <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.

## <a name="see-also"></a>Viz také
- [Třída úkolu](../../extensibility/debugger/task-class-internal-members.md)
