---
description: Tato metoda vyhodnocuje výraz asynchronně.
title: 'IDebugExpression2:: EvaluateAsync | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bea7a5a05dc5277e693d033452f0b4e7342ea946
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092420"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Tato metoda vyhodnocuje výraz asynchronně.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EvaluateAsync (
    EVALFLAGS             dwFlags,
    IDebugEventCallback2* pExprCallback
);
```

```csharp
int EvaluateAsync(
    enum_EVALFLAGS       dwFlags,
    IDebugEventCallback2 pExprCallback
);
```

## <a name="parameters"></a>Parametry
`dwFlags`\
pro Kombinace příznaků z výčtu [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) , který ovládá vyhodnocení výrazu.

`pExprCallback`\
pro Tento parametr je vždycky hodnota null.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby. Typický kód chyby:

|Chyba|Popis|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|V tuto chvíli se vyhodnocuje jiný výraz a hodnocení souběžného výrazu se nepodporuje.|

## <a name="remarks"></a>Poznámky
Tato metoda by se měla vrátit hned po spuštění vyhodnocení výrazu. Po úspěšném vyhodnocení výrazu [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) musí být do zpětného volání události [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) odesílána jako dodaná prostřednictvím [připojení](../../../extensibility/debugger/reference/idebugprogram2-attach.md) nebo [připojení](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro jednoduchý `CExpression` objekt, který implementuje rozhraní [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) .

```cpp
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,
                                   IDebugEventCallback2* pExprCallback)
{
    // Set the aborted state to FALSE
    // in case the user tries to redo the evaluation after aborting.
    m_bAborted = FALSE;
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.
    // This starts the expression evaluation on a background thread.
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);
    return S_OK;
}
```

## <a name="see-also"></a>Viz také
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
