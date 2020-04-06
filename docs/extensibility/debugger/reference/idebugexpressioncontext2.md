---
title: IDebugExpressionContext2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 344ae287b3784ceca87fbbab09ad2b2e0a304205
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729638"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Toto rozhraní představuje kontext pro vyhodnocení výrazu.

## <a name="syntax"></a>Syntaxe

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představují kontext, ve kterém lze vyhodnocovat výraz.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) vrátí toto rozhraní. Toto rozhraní je přístupné pouze v případě, že byl laděný program pozastaven a je k dispozici rámec zásobníku.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugExpressionContext2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Načte název kontextu hodnocení.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analyzuje textový výraz pro vyhodnocení.|

## <a name="remarks"></a>Poznámky
 Kontext hodnocení lze považovat za obor pro provádění vyhodnocení výrazu.

 Pokud program byl zastaven, správce ladění relace (SDM) získá rámec zásobníku z DE s voláním [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). SDM pak volá [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) `IDebugExpressionContext2` získat rozhraní. Následuje volání [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) k vytvoření rozhraní [IDebugExpression2,](../../../extensibility/debugger/reference/idebugexpression2.md) které představuje analyzovaný výraz připravený k vyhodnocení.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
