---
description: Úloha byla zrušena dříve, než dosáhla stavu spuštění, nebo potvrdila zrušení a dokončení bez výjimky.
title: TASK_STATE_CANCELED pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8e99148c223f86a0307a0588e7803a5fadf52d6a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223326"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED pole
Úloha byla zrušena dříve, než dosáhla stavu spuštění, nebo potvrdila zrušení a dokončení bez výjimky.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v mscorlib.dll)

 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členovi z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Poznámky
 Pokud pole [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) obsahuje tuto hodnotu, <xref:System.Threading.Tasks.Task.Status%2A> vlastnost vrátí hodnotu <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Viz také
- [Task – třída](../../extensibility/debugger/task-class-internal-members.md)
