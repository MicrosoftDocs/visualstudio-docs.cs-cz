---
title: IDebugExpression2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2e23ad4f673e4e150ea677d993c5b36a4e386c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729687"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Toto rozhraní představuje analyzovaný výraz připravený pro vazbu a vyhodnocení.

## <a name="syntax"></a>Syntaxe

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představující analyzovaný výraz připravený k vyhodnocení.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) vrátí toto rozhraní. [Funkce GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) vrátí rozhraní [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Tato rozhraní jsou přístupná pouze v případě, že byl program, který je laděn, pozastaven a je k dispozici rámec zásobníku.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugExpression2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Vyhodnotí tento výraz asynchronně.|
|[Přerušení](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Ukončí vyhodnocení asynchronního výrazu.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Vyhodnotí tento výraz synchronně.|

## <a name="remarks"></a>Poznámky
 Pokud program byl zastaven, správce ladění relace (SDM) získá rámec zásobníku z DE s voláním [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). SDM pak volá [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) získat rozhraní [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Následuje volání [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) k vytvoření `IDebugExpression2` rozhraní, které představuje analyzovaný výraz připravený k vyhodnocení.

 SDM volá buď [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) skutečně vyhodnotit výraz a vytvořit hodnotu.

 V implementaci `IDebugExpressionContext2::ParseText`aplikace de používá `CoCreateInstance` funkci COM k vytvoření instance vyhodnocení výrazu a získání rozhraní [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) (viz příklad v `IDebugExpressionEvaluator` rozhraní). DE pak volá [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) získat rozhraní [IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md) Toto rozhraní se používá `IDebugExpression2::EvaluateSync` `IDebugExpression2::EvaluateAsync` při implementaci a provedení vyhodnocení.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
