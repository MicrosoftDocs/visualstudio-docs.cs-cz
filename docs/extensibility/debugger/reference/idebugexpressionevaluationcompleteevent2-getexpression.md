---
title: IDebugExpressionEvaluationCompleteEvent2::GetExpression
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetExpression
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetExpression
ms.assetid: faf6b2dd-2afd-4852-b21c-7e8d3130e141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d938b2081081f0fd3821ebea2e12d39a9ef6a185
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038527"
---
# <a name="idebugexpressionevaluationcompleteevent2getexpression"></a>IDebugExpressionEvaluationCompleteEvent2::GetExpression
Získá původní výraz.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetExpression( 
   IDebugExpression2** ppExpr
);
```

```csharp
int GetExpression( 
   out IDebugExpression2 ppExpr
);
```

## <a name="parameters"></a>Parametry
`ppExpr`\
mimo Vrátí objekt [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) , který představuje analyzovaný výraz.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda vrátí objekt, který byl vytvořen voláním metody [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) .

## <a name="see-also"></a>Viz také
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
