---
title: Metoda NotifyDebuggerOfWaitCompletion | Microsoft Docs
description: Přečtěte si o metodě NotifyDebuggerOfWaitCompletion, která je zástupný symbol použitý jako cíl zarážky v ladicím programu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 35571b28287ecdea48a2ff089cb25cf3ed742d60
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606629"
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
