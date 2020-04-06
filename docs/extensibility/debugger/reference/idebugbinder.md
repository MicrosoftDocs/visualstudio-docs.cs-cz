---
title: IDebugBinder | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735968"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní váže pole symbolu, obvykle vrácené zprostředkovatelem symbolu, s kontextem paměti nebo objektem, který obsahuje aktuální hodnotu symbolu.

## <a name="syntax"></a>Syntaxe

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní podporuje vyhodnocení výrazu a musí být implementováno ladicímodul (DE).

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní se používá v procesu vyhodnocení výrazu a obvykle se používá při implementaci [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) a [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugBinder`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Vytvořit vazbu](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Získá kontext paměti nebo objekt, který obsahuje aktuální hodnotu symbolu.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Určuje typ objektu za běhu.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Převede umístění objektu nebo adresu paměti na kontext paměti.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Získá objekt [IDebugFunctionObject,](../../../extensibility/debugger/reference/idebugfunctionobject.md) který slouží k vytvoření parametrů funkce.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Získá přesný typ proměnné.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní vrátí objekty, které jsou používány vyhodnocení výrazu ve stromech analýzy. Vyhodnocení výrazu analyzuje výraz pomocí zprostředkovatele symbolu k převodu symbolů ve výrazu na instance [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), které popisují každý symbol z hlediska jeho typu a umístění ve zdrojovém kódu. Metoda [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) převede objekty na objekty `IDebugField` [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) které spojují nebo vážou typ symbolu na skutečnou hodnotu v paměti. Tyto `IDebugObject` objekty jsou pak uloženy ve stromu analýzy pro pozdější vyhodnocení.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
