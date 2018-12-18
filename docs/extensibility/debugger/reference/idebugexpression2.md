---
title: IDebugExpression2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8cd5dcce6f81e8f61f13cc09dffb460449b0deae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114635"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Toto rozhraní představuje Analyzovaná výraz připravené pro vazby a vyhodnocení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Modul ladění (DE) implementuje toto rozhraní představují výraz analyzovaný připravené k vyhodnocení.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Volání [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) vrátí toto rozhraní. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) vrátí [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) rozhraní. Tato rozhraní jsou přístupné jenom v případě, že byla pozastavena programu laděné a rámce zásobníku je k dispozici.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDebugExpression2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Tento výraz vyhodnotí asynchronně.|  
|[Přerušení](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Ukončí asynchronní výraz vyhodnocení.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Tento výraz vyhodnotí synchronně.|  
  
## <a name="remarks"></a>Poznámky  
 Když program se zastavil, správce ladicí relace (SDM) získává rámce zásobníku z DE pomocí volání [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Pak zavolá SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) získat [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) rozhraní. Následují volání [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) vytvořit `IDebugExpression2` rozhraní, což představuje Analyzovaná výraz, který je připraven k vyhodnocení.  
  
 SDM zavolá buď [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ve skutečnosti vyhodnocování výrazu a vytvoření hodnoty.  
  
 V implementaci `IDebugExpressionContext2::ParseText`, DE používá COM na `CoCreateInstance` funkce k vytvoření instance vyhodnocovací filtr výrazů a získat [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) rozhraní (podívejte se na příklad v `IDebugExpressionEvaluator` rozhraní). DE pak zavolá [analyzovat](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) získat [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) rozhraní. Toto rozhraní se používá při provádění `IDebugExpression2::EvaluateSync` a `IDebugExpression2::EvaluateAsync` k vyhodnocení.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)