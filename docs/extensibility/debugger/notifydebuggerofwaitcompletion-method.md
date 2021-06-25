---
title: NotifyDebuggerOfWaitCompletion – metoda | Microsoft Docs
description: Přečtěte si o metodě NotifyDebuggerOfWaitCompletion, což je zástupný symbol používaný ladicím programem jako cíl zarážky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b9d6b5fbdcb8195709a751117056bcaa0617eff
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904214"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Metoda NotifyDebuggerOfWaitCompletion
Metoda zástupného symbolu použitá ladicím programem jako cíl zarážky. Tato metoda nesmí být inlindována ani optimalizována.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

## <a name="syntax"></a>Syntax

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Poznámky
 Všechny operace spojení s úlohou by měly tuto metodu volat, pokud je nastaven bit oznámení ladicího programu.

## <a name="requirements"></a>Požadavky

## <a name="see-also"></a>Viz také
- [Task – třída](../../extensibility/debugger/task-class-internal-members.md)
