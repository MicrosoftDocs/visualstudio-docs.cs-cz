---
title: SetNotificationForWaitCompletion Metoda | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226ac41c8e3b7427ac3b9aba7bea08dbb7329d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712865"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion – metoda
Nastaví nebo vymaže bit stavu TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestava:** mscorlib (v *mscorlib.dll*)

## <a name="syntax"></a>Syntaxe

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parametry
 `enabled`

 `true`pro nastavení bitu; `false` pro odstavení bitu.

## <a name="exceptions"></a>Výjimky

## <a name="remarks"></a>Poznámky
 Ladicí program nastaví tento bit, aby pomohl vystoupit z těla asynchronní metody. Pokud `enabled` `true`je , tato metoda musí být volána pouze na úkol, který ještě nebyl dokončen. Pokud `enabled` `false`je , tato metoda může být volána na dokončené úkoly. V obou těchto případě by měl být použit pouze pro úkoly ve stylu příslibu.

## <a name="requirements"></a>Požadavky

## <a name="see-also"></a>Viz také
- [Třída úkolu](../../extensibility/debugger/task-class-internal-members.md)
