---
title: Metoda SetNotificationForWaitCompletion | Microsoft Docs
description: Přečtěte si, jak ladicí program používá stavový bit pro podrobnou krok textu asynchronní metody pro úlohy ve stylu Promise.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2418e958c027fea7fd39c93b0d5abbd95d64435b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960789"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion – metoda
Nastaví nebo vymaže bit stavu TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

## <a name="syntax"></a>Syntaxe

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parametry
 `enabled`

 `true` nastavení bitu; `false` Chcete-li zrušit nastavení bitu.

## <a name="exceptions"></a>Výjimky

## <a name="remarks"></a>Poznámky
 Ladicí program nastaví tento bit tak, aby pomohly krokovat tělo asynchronní metody. Pokud `enabled` má hodnotu `true` , tato metoda musí být volána pouze pro úkol, který ještě nebyl dokončen. `enabled` `false` V takovém případě lze tuto metodu volat u dokončených úloh. V obou případech by se měla použít jenom pro úlohy ve stylu Promise.

## <a name="requirements"></a>Požadavky

## <a name="see-also"></a>Viz také
- [Task – třída](../../extensibility/debugger/task-class-internal-members.md)
