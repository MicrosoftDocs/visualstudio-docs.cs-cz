---
title: Implementace vyhodnocení výrazu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8c7c9a1130794dd4c28f212afd6cb3c030f5a1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738542"
---
# <a name="implement-an-expression-evaluator"></a>Implementace vyhodnocení výrazu
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Vyhodnocení výrazu je složitá souhra mezi ladicím strojem (DE), zprostředkovatelem symbolu (SP), objektem pořadače a vyhodnocením výrazu (EE). Tyto čtyři součásti jsou propojeny rozhraními, které jsou implementovány jednou komponentou a spotřebovány jinou.

 EE bere výraz z DE ve formě řetězce a analyzuje nebo vyhodnocuje. EE spouští následující rozhraní, která de spotřebovává:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE volá objekt pořadače, dodaný DE, chcete-li získat hodnotu symbolů a objektů. EE spotřebovává následující rozhraní, které jsou implementovány DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE spustí [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`Poskytuje mechanismus pro popis výsledku vyhodnocení výrazu, jako je například místní proměnná, primitivní nebo objekt visual studio, který pak zobrazí příslušné informace v **locals**, **Watch**nebo **Immediate** okno.

  Sp je dána EE de, když žádá o informace. Sp spustí rozhraní, která popisují adresy a pole, jako jsou následující rozhraní a jejich deriváty:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE spotřebovává všechna tato rozhraní.

## <a name="in-this-section"></a>V tomto oddílu
 [Strategie implementace vyhodnocení výrazu](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Definuje třístupňový proces pro strategii implementace vyhodnocení výrazu (EE).

## <a name="see-also"></a>Viz také
- [Zápis vyhodnocení výrazu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
