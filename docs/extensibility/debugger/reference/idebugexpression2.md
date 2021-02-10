---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d7b6508a635edf3dc328f79a06a386efce07aae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949581"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Toto rozhraní představuje analyzovaný výraz připravený pro vazbu a hodnocení.

## <a name="syntax"></a>Syntax

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní, aby představovalo vyhodnocený výraz, který je připravený k vyhodnocení.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní vrátí volání [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) vrátí rozhraní [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Tato rozhraní jsou přístupná pouze v případě, že je program laděn a je k dispozici rámec zásobníku.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugExpression2` .

|Metoda|Popis|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Vyhodnotí tento výraz asynchronně.|
|[Přerušit](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Ukončí vyhodnocení asynchronního výrazu.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Vyhodnotí tento výraz synchronně.|

## <a name="remarks"></a>Poznámky
 Po zastavení programu Správce ladění relace (SDM) získá rámec zásobníku z DE s voláním metody [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Model SDM pak zavolá [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) , aby získal rozhraní [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Toto je následováno voláním [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) k vytvoření `IDebugExpression2` rozhraní, které představuje analyzovaný výraz připravený k vyhodnocení.

 Model SDM zavolá buď [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , ke skutečnému vyhodnocení výrazu a vytvoření hodnoty.

 V implementaci nástroje `IDebugExpressionContext2::ParseText` de používá funkci modelu COM `CoCreateInstance` k vytvoření instance vyhodnocovacího filtru výrazů a získání rozhraní [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) (viz příklad v `IDebugExpressionEvaluator` rozhraní). DE then rozvolá [analýzu](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) , aby získala rozhraní [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) . Toto rozhraní se používá v implementaci `IDebugExpression2::EvaluateSync` a `IDebugExpression2::EvaluateAsync` k provedení vyhodnocení.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
