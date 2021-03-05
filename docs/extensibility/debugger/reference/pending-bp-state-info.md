---
description: Obsahuje informace o stavu zarážky, která je připravena k vytvoření vazby na umístění kódu.
title: PENDING_BP_STATE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edd4bbdde1c241d90329343be1fd5570129c675a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223924"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
Obsahuje informace o stavu zarážky, která je připravena k vytvoření vazby na umístění kódu.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagPENDING_BP_STATE_INFO { 
   PENDING_BP_STATE       state;
   PENDING_BP_STATE_FLAGS flags;
} PENDING_BP_STATE_INFO;
```

```csharp
public struct PENDING_BP_STATE_INFO { 
   public uint state;
   public uint flags;
};
```

## <a name="members"></a>Členové
 `state`\
 Hodnota z výčtu [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) , která určuje stav čeká na zarážce.

 `flags`\
 Kombinace příznaků z výčtu [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) , která určuje, zda je zarážka virtualizovaná.

## <a name="remarks"></a>Poznámky
 Tato struktura je předána metodě [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) , kde je vyplněna.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
