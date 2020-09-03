---
title: Vyhodnocení výrazu v režimu přerušení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 362e50e20519c358564d13ba169f706fe384ca5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152762"
---
# <a name="expression-evaluation-in-break-mode"></a>Vyhodnocení výrazu v režimu přerušení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následující článek popisuje proces, který nastane, když je ladicí program v režimu pozastavení a musí provádět vyhodnocení výrazu.  
  
## <a name="expression-evaluation-process"></a>Proces vyhodnocení výrazu  
 Toto jsou základní kroky, které jsou součástí vyhodnocení výrazu:  
  
1. Správce ladění relace (SDM) volá [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) , aby získal kontextový rozhraní výrazu [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2. Model SDM pak zavolá [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) s řetězcem, který se má analyzovat.  
  
3. Pokud ParseText nevrátí S_OK, je vrácen důvod chyby.  
  
     případech  
  
     Pokud ParseText vrátí S_OK, SDM může následně zavolat buď [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , aby získala konečnou hodnotu z analyzovaného výrazu.  
  
    - V případě použití `IDebugExpression2::EvaluateSync` je dané rozhraní zpětného volání používáno pro komunikaci průběžného procesu vyhodnocení. Konečná hodnota se vrátí v rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
    - V případě použití `IDebugExpression2::EvaluateAsync` je dané rozhraní zpětného volání používáno pro komunikaci průběžného procesu vyhodnocení. Po dokončení vyhodnocení EvaluateAsync odešle rozhraní [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) prostřednictvím zpětného volání. S tímto rozhraním události lze konečnou hodnotu získat pomocí [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Viz také  
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
