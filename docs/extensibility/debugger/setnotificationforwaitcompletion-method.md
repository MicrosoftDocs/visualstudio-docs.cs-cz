---
title: Metoda SetNotificationForWaitCompletion | Microsoft Docs
description: Přečtěte si, jak ladicí program používá stavový bit pro podrobnou krok textu asynchronní metody pro úlohy ve stylu Promise.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ec469ed4f9c4fa2e503b2350235299a81a94bf9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902108"
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
