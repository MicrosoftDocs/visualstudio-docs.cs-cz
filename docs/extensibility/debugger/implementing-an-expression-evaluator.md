---
title: Implementace vyhodnocovacího filtru výrazů | Microsoft Docs
description: Přečtěte si o vyhodnocení výrazu, který zahrnuje ladicí stroj, poskytovatele symbolů, objekt pořadače a vyhodnocovací filtr výrazů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 121bd17e2343cfbba509e85d78ba37b57964f895
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947668"
---
# <a name="implement-an-expression-evaluator"></a>Implementace vyhodnocovacího filtru výrazů
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Vyhodnocení výrazu je komplexní souhře mezi ladicím strojem (DE), zprostředkovatelem symbolu (SP), objektem pořadače a vyhodnocovacím filtrem výrazů (EE). Tyto čtyři komponenty jsou propojeny rozhraními, která jsou implementována jednou komponentou a jsou využívána jinou.

 EE přebírá výraz z DE ve formě řetězce a analyzuje nebo vyhodnocuje. V EE jsou spouštěna následující rozhraní, která jsou spotřebovaná pomocí DE:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE volá objekt pořadače dodaný DE, aby získal hodnotu symbolů a objektů. EE používá následující rozhraní, která jsou implementována pomocí DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  V EE se spustí [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` poskytuje mechanismus pro popis výsledku vyhodnocení výrazu, jako je například místní proměnná, primitivum nebo objekt do sady Visual Studio, který pak zobrazí příslušné informace v oknech **místní** hodnoty, **kukátko** nebo **okamžité** .

  Tato aktualizace je uvedena v EE pomocí DE, když se požádá o informace. SP spouští rozhraní, která popisují adresy a pole, například následující rozhraní a jejich deriváty:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  V EE se spotřebovávají všechna tato rozhraní.

## <a name="in-this-section"></a>V této části
 [Strategie implementace vyhodnocovacího filtru výrazů](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Definuje proces tří kroků pro strategii pro implementaci vyhodnocovacího filtru výrazů (EE).

## <a name="see-also"></a>Viz také
- [Zápis vyhodnocovacího filtru výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
