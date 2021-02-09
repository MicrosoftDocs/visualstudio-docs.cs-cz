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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b62b613950f9fd6c8ce18969c126a6e74a154b58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851293"
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
