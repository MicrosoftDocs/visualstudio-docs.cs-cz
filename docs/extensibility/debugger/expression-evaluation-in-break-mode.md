---
title: Vyhodnocení výrazu v režimu přerušení | Microsoft Docs
description: Přečtěte si o procesu, ke kterému dochází, když je ladicí program v režimu pozastavení a musí provádět vyhodnocení výrazu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 932bebecf4eea73cfae579bbea58e024b4388ffb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067865"
---
# <a name="expression-evaluation-in-break-mode"></a>Vyhodnocení výrazu v režimu přerušení
Následující část popisuje proces, který nastane, když je ladicí program v režimu pozastavení a musí provádět vyhodnocení výrazu.

## <a name="expression-evaluation-process"></a>Proces vyhodnocení výrazu
 Níže jsou uvedené základní kroky pro vyhodnocení výrazu:

1. Správce ladění relace (SDM) volá [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) , aby získal kontextový rozhraní výrazu [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. Model SDM pak zavolá [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) s řetězcem, který se má analyzovat.

3. Pokud ParseText nevrátí S_OK, je vrácen důvod chyby.

     případech

     Pokud ParseText vrátí S_OK, SDM může následně zavolat buď [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , aby se získala konečná hodnota z analyzovaného výrazu.

    - Při použití `IDebugExpression2::EvaluateSync` aplikace přenáší dané rozhraní zpětného volání průběžný proces vyhodnocení. Konečná hodnota se vrátí v rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .

    - Při použití `IDebugExpression2::EvaluateAsync` aplikace přenáší dané rozhraní zpětného volání průběžný proces vyhodnocení. Po dokončení vyhodnocení EvaluateAsync odešle rozhraní [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) prostřednictvím zpětného volání. S tímto rozhraním události výsledná hodnota vyplývají z [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Viz také
- [Události ladicího programu volání](../../extensibility/debugger/calling-debugger-events.md)
