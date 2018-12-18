---
title: Vyhodnocení výrazu v režimu pozastavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4afa0f98616ebcb85d421874b9c6ed5cc7270b52
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232977"
---
# <a name="expression-evaluation-in-break-mode"></a>Vyhodnocení výrazu v režimu pozastavení
Následující část popisuje proces, který nastane, pokud je v režimu přerušení ladicího programu a musí provést vyhodnocení výrazu.  
  
## <a name="expression-evaluation-process"></a>Proces vyhodnocení výrazu  
 Toto jsou základní kroky při vyhodnocení výrazu:  
  
1.  Správce ladění relace (SDM) volá [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) získat rozhraní kontextu výrazu [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Pak zavolá SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) s řetězcem, který se má analyzovat.  
  
3.  Pokud ParseText nevrací hodnotu S_OK, vrátí se z důvodu chyby.  
  
     -jinak-  
  
     Pokud ParseText nevrátí hodnotu S_OK, SDM pak můžete volat buď [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) zobrazíte konečnou hodnotu z analyzovaného výrazu.  
  
    -   Při použití `IDebugExpression2::EvaluateSync`, daného zpětného volání rozhraní komunikuje probíhající proces hodnocení. Konečná hodnota se vrátí v [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) rozhraní.  
  
    -   Při použití `IDebugExpression2::EvaluateAsync`, daného zpětného volání rozhraní komunikuje probíhající proces hodnocení. Po dokončení hodnocení EvaluateAsync odešle [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) rozhraní zpětného volání. S tímto rozhraním události konečná hodnota výsledky s [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Viz také:  
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)