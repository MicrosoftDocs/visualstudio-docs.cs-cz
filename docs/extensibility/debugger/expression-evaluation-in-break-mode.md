---
title: Vyhodnocení výrazu v režimu přerušení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc09fc43bd9f0edea4f6dc32e5f37c387c045796
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738731"
---
# <a name="expression-evaluation-in-break-mode"></a>Vyhodnocení výrazu v režimu přerušení
Následující část popisuje proces, ke kterému dochází, když je ladicí program v režimu přerušení a musí provést vyhodnocení výrazu.

## <a name="expression-evaluation-process"></a>Proces vyhodnocení výrazu
 Následují základní kroky při vyhodnocování výrazu:

1. Správce ladění relace (SDM) volá [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) získat kontextové rozhraní [výrazu, IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. SDM pak volá [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) s řetězcem, který má být analyzován.

3. Pokud ParseText nevrátí S_OK, je vrácendůvod chyby.

     -jinak-

     Pokud ParseText vrátí S_OK, může sdm pak volat buď [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) získat konečnou hodnotu z analyzovaného výrazu.

    - Při `IDebugExpression2::EvaluateSync`použití , dané rozhraní zpětného volání komunikuje probíhající proces hodnocení. Konečná hodnota je vrácena v rozhraní [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

    - Při `IDebugExpression2::EvaluateAsync`použití , dané rozhraní zpětného volání komunikuje probíhající proces hodnocení. Po dokončení vyhodnocení EvaluateAsync odešle rozhraní [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) prostřednictvím zpětného volání. S tímto rozhraním události konečné hodnoty výsledky s [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
