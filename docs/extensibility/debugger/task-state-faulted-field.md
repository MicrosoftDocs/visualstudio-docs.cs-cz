---
description: Úloha byla dokončena z důvodu neošetřené výjimky.
title: TASK_STATE_FAULTED pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5a8113f6145706d2863a4f0060a8627952eb0b3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223183"
---
# <a name="task_state_faulted-field"></a>TASK_STATE_FAULTED pole
Úloha byla dokončena z důvodu neošetřené výjimky.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členovi z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)
```

## <a name="remarks"></a>Poznámky
 Pokud pole [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) obsahuje tuto hodnotu, <xref:System.Threading.Tasks.Task.Status%2A> vlastnost vrátí hodnotu <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Viz také
- [Task – třída](../../extensibility/debugger/task-class-internal-members.md)
