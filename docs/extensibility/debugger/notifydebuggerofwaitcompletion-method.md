---
title: Metoda NotifyDebuggerOfWaitCompletion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8963e29a067754c0e8c89b9db336b239ac682ce1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738333"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Metoda NotifyDebuggerOfWaitCompletion
Zástupná metoda použitá jako cíl zarážky v ladicím programu. Tato metoda nesmí být vložená ani optimalizovaná.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

## <a name="syntax"></a>Syntax

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Poznámky
 Všechny operace join s úkolem by měly volat tuto metodu, pokud je nastaven bit oznámení ladicího programu.

## <a name="requirements"></a>Požadavky

## <a name="see-also"></a>Viz také
- [Task – třída](../../extensibility/debugger/task-class-internal-members.md)
