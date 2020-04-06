---
title: Vyhodnocení výrazu okna kukátka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cef2f27eec095ee7b136153ecb764feba9effbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738848"
---
# <a name="evaluate-a-watch-window-expression"></a>Vyhodnocení výrazu okna kukátka
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Při pozastavení spuštění Visual Studio volá ladicí modul (DE) k určení aktuální hodnoty každého výrazu v seznamu sledovaných položek. DE vyhodnotí každý výraz pomocí vyhodnocení výrazu (EE) a Visual Studio zobrazí jeho hodnotu v okně **kukátka.**

 Následuje přehled způsobu vyhodnocení výrazu seznamu sledovaných položek:

1. Visual Studio volá DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) získat kontext výrazu, který lze použít k vyhodnocení výrazů.

2. Pro každý výraz v seznamu sledovaných volání Sady Visual Studio [parseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) převést text výrazu do analyzovaného výrazu.

3. `IDebugExpressionContext2::ParseText`volá [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) provést skutečnou práci analýzy textu a vytvořit [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objektu.

4. `IDebugExpressionContext2::ParseText`vytvoří objekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) a `IDebugParsedExpression` vloží do něj objekt. Tento`DebugExpression2` I objekt je pak vrácena do sady Visual Studio.

5. Visual Studio volá [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) vyhodnotit analyzovaný výraz.

6. `IDebugExpression2::EvaluateSync`Předá volání [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) provést skutečné vyhodnocení a vytvořit [objekt IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) který je vrácen do sady Visual Studio.

7. Visual Studio volá [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) získat hodnotu výrazu, který je pak zobrazen v seznamu sledovaných.

## <a name="parse-then-evaluate"></a>Analýza pak vyhodnocuje
 Vzhledem k tomu, že analýza komplexní výraz může trvat mnohem déle, než jeho vyhodnocení, proces vyhodnocení výrazu je rozdělendo dvou kroků: 1) analyzovat výraz a 2) vyhodnotit analyzovaný výraz. Tímto způsobem hodnocení může dojít mnohokrát, ale výraz je třeba analyzovat pouze jednou. Zprostředkující analyzovaný výraz je vrácen z EE v objektu [IDebugParsedExpression,](../../extensibility/debugger/reference/idebugparsedexpression.md) který je zase zapouzdřen a vrácen z DE jako objekt [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md) Objekt `IDebugExpression` odloží všechny `IDebugParsedExpression` hodnocení objektu.

> [!NOTE]
> Není nutné pro EE dodržovat tento dvoustupňový proces, i když Visual Studio předpokládá toto; EE můžete analyzovat a vyhodnotit ve stejném kroku při [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) se nazývá (to je, jak mycee ukázka funguje, například). Pokud váš jazyk může tvořit složité výrazy, můžete oddělit krok analýzy od kroku hodnocení. To může zvýšit výkon v ladicím programu sady Visual Studio při zobrazení mnoha výrazů sledování.

## <a name="in-this-section"></a>V tomto oddílu
 [Ukázková implementace vyhodnocení exprese](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Používá mycee ukázku krokovat proces vyhodnocení výrazu.

 [Vyhodnocení výrazu sledování](../../extensibility/debugger/evaluating-a-watch-expression.md) Vysvětluje, co se stane po úspěšném výrazu analýzy.

## <a name="related-sections"></a>Související oddíly
 [Souvislosti hodnocení](../../extensibility/debugger/evaluation-context.md) Poskytuje argumenty, které jsou předány při ladění motoru (DE) volá vyhodnocení výrazu (EE).

## <a name="see-also"></a>Viz také
 [Zápis vyhodnocení výrazu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
