---
title: IDebugParsedExpression | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22069b8eedb06d67eafaf7333f379a057c1b6f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725992"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní představuje analyzovaný výraz připravený k vyhodnocení.

## <a name="syntax"></a>Syntaxe

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocení výrazu implementuje toto rozhraní představují analyzovaný výraz, který je připraven k vyhodnocení.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [Analýzy](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) vrátí toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce je `IDebugParsedExpression`uvedena metoda .

|Metoda|Popis|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Vyhodnotí analyzovaný výraz.|

## <a name="remarks"></a>Poznámky
 Když volající je připraven k vyhodnocení výrazu, volá [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) vrátit [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) který obsahuje výsledek vyhodnocení. Tento dvoudílný přístup k vyhodnocení, analýza pak vyhodnocení, umožňuje analyzovaný výraz, které mají být vyhodnoceny vícekrát, obcházet časově náročný proces analýzy výrazu.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
