---
title: Rozhraní key expression evaluators | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01527edac4000f0b2f7b89fdd507fc093f0d7734
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738486"
---
# <a name="key-expression-evaluator-interfaces"></a>Rozhraní hodnotitele klíčových výrazů
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Při psaní vyhodnocení výrazu (EE), spolu s kontextu vyhodnocení, měli byste být obeznámeni s následujícími rozhraními.

## <a name="interface-descriptions"></a>Popisy rozhraní

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Má jednu metodu [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), která získá datovou strukturu, která představuje aktuální bod spuštění. Tato datová struktura je jedním ze tří argumentů, které ladicí modul (DE) předá metodě [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) k vyhodnocení výrazu. Toto rozhraní je obvykle implementováno zprostředkovatelem symbolu.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Má [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) metoda, která získá oblast paměti, která obsahuje aktuální hodnotu symbolu. Vzhledem k tomu, jak obsahující metoda, reprezentované [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objektu a `IDebugBinder::Bind` symbol sám, reprezentované [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objektu, vrátí hodnotu symbolu. `IDebugBinder`je obvykle implementována DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Představuje jednoduchý datový typ. Pro složitější typy, jako jsou pole a metody, použijte odvozené rozhraní [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) a [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) je další důležité odvozené rozhraní, které představuje symboly obsahující jiné symboly, jako jsou metody nebo třídy. Rozhraní `IDebugField` (a jeho deriváty) je obvykle implementováno poskytovatelem symbolu.

     Objekt `IDebugField` lze najít název a typ symbolu a spolu s [objektem IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) lze použít k nalezení jeho hodnoty.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Představuje skutečné bity hodnoty za běhu symbolu. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) trvá [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objekt, který představuje symbol a vrátí [Objekt IDebugObject.](../../extensibility/debugger/reference/idebugobject.md) Metoda [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) vrátí hodnotu symbolu ve vyrovnávací paměti. De obvykle implementuje toto rozhraní představují hodnotu vlastnosti v paměti.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Toto rozhraní představuje samotný vyhodnocení výrazu. Key Metoda je [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), který vrátí [rozhraní IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Toto rozhraní představuje analyzovaný výraz připravený k vyhodnocení. Key Metoda je [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) který vrátí IDebugProperty2 představující hodnotu a typ výrazu.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Toto rozhraní představuje hodnotu a její typ a je výsledkem vyhodnocení výrazu.

## <a name="see-also"></a>Viz také
- [Souvislosti hodnocení](../../extensibility/debugger/evaluation-context.md)
