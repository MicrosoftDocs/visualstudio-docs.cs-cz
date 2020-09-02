---
title: IDebugBinder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcdec19c4667356edaf9e057c86ddc24baf747b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735968"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní váže pole symbolu, které obvykle vrací poskytovatel symbolů, do paměťového kontextu nebo objektu, který obsahuje aktuální hodnotu symbolu.

## <a name="syntax"></a>Syntax

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní podporuje vyhodnocení výrazu a musí být implementováno ladicím modulem (DE).

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní se používá v procesu vyhodnocení výrazu a obvykle se používá v implementaci [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) a [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugBinder` .

|Metoda|Popis|
|------------|-----------------|
|[Zapisovat](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Získá kontext paměti nebo objekt, který obsahuje aktuální hodnotu symbolu.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Určuje typ běhu objektu.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Převede umístění objektu nebo adresu paměti na kontext paměti.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Získá objekt [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) , který se používá k vytvoření parametrů funkce.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Získá přesný typ pro proměnnou.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní vrací objekty, které jsou používány vyhodnocovacím filtrem výrazů ve stromech analýzy. Vyhodnocení výrazu analyzuje výraz pomocí poskytovatele symbolů pro převod symbolů ve výrazu na instance [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), které popisují každý symbol z podmínek jeho typu a umístění ve zdrojovém kódu. Metoda [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md) převede `IDebugField` objekty na objekty [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , které spojují nebo vážou typ symbolu se skutečnou hodnotou v paměti. Tyto `IDebugObject` objekty jsou následně uloženy ve stromové struktuře analýzy pro pozdější vyhodnocení.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
