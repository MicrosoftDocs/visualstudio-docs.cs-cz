---
title: IDebugExpressionContext2 | Microsoft Docs
description: Toto rozhraní představuje kontext pro vyhodnocení výrazu.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6d8745207f1ab075aedd43815e7a97a4f0721bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092290"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Toto rozhraní představuje kontext pro vyhodnocení výrazu.

## <a name="syntax"></a>Syntax

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní, aby představovalo kontext, ve kterém lze výraz vyhodnotit.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) vrací toto rozhraní. Toto rozhraní je přístupné pouze v případě, že je program laděn a je k dispozici rámec zásobníku.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugExpressionContext2` .

|Metoda|Popis|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Načte název kontextu vyhodnocení.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analyzuje textový výraz pro vyhodnocení.|

## <a name="remarks"></a>Poznámky
 Kontext vyhodnocení lze představit jako obor pro provádění vyhodnocení výrazu.

 Po zastavení programu Správce ladění relace (SDM) získá rámec zásobníku z DE s voláním metody [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Model SDM pak zavolá [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) , aby získal `IDebugExpressionContext2` rozhraní. Toto je následováno voláním [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) k vytvoření rozhraní [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) , které představuje analyzovaný výraz připravený k vyhodnocení.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
