---
title: Ukázková implementace vyhodnocení výrazu | Microsoft Docs
description: Přečtěte si, jak Visual Studio volá ParseText k vytvoření objektu IDebugExpression2 pro kukátko výrazu Windows.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 60d01917bb3a21f6d8ea2644fbeef2b22064cc00
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070450"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Ukázková implementace vyhodnocení výrazu
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Pro výraz okna **kukátka** aplikace Visual Studio volá [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) k vytvoření objektu [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpressionContext2::ParseText` Vytvoří instanci vyhodnocovacího filtru výrazů (EE) a zavolá [analýzu](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) , aby získala objekt [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .

 `IDebugExpressionEvaluator::Parse`Provádí následující úlohy:

1. [Pouze C++] Analyzuje výraz pro hledání chyb.

2. Vytvoří instanci třídy ( `CParsedExpression` v tomto příkladu se volá), která spustí `IDebugParsedExpression` rozhraní a uloží do třídy výraz, který se má analyzovat.

3. Vrátí `IDebugParsedExpression` rozhraní z `CParsedExpression` objektu.

> [!NOTE]
> V příkladech, které následují a v ukázce mycee, vyhodnocovací filtr výrazů odděluje analýzu od vyhodnocení.

## <a name="managed-code"></a>Spravovaný kód
 Následující kód ukazuje implementaci `IDebugExpressionEvaluator::Parse` ve spravovaném kódu. Tato verze metody odkládá analýzu na [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , protože kód pro analýzu se také vyhodnocuje ve stejnou dobu (viz [vyhodnocení výrazu kukátko](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Nespravovaný kód
Následující kód je implementace `IDebugExpressionEvaluator::Parse` v nespravovaném kódu. Tato metoda volá pomocnou funkci, `Parse` , k analýze výrazu a kontrole chyb, ale tato metoda ignoruje výslednou hodnotu. Formální vyhodnocení se odloží na [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , kde se při vyhodnocování výrazu analyzuje (viz [vyhodnocení výrazu kukátka](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>Viz také
- [Vyhodnocení výrazu okno Kukátko](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Vyhodnocení výrazu kukátka](../../extensibility/debugger/evaluating-a-watch-expression.md)
