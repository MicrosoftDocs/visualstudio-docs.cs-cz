---
title: IDebugExpression2::Přerušit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de2e34a8ae1e038c2109627099dacc5bd03a1ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729772"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Tato metoda zruší vyhodnocení asynchronního výrazu, jak bylo spuštěno voláním metody [EvaluateAsync.](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Abort(
   void
);
```

```csharp
int Abort();
```

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Při zrušení vyhodnocení asynchronního výrazu neodesílejte událost [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) zpětnému volání události předané metodám [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) nebo [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="see-also"></a>Viz také
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
