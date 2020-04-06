---
title: Ukázková implementace vyhodnocení exprese | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf994a61ed9283463cd01aa468018f6acce5e209
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713101"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Ukázková implementace vyhodnocení exprese
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Pro výraz okno **Watch** Visual Studio volá [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) k vytvoření objektu [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugExpressionContext2::ParseText`instance vyhodnocení výrazu (EE) a volá [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) získat [Objekt IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

 Provádí `IDebugExpressionEvaluator::Parse` následující úkoly:

1. [Pouze C++] Analyzuje výraz hledat chyby.

2. Vytvoří instance třídy (nazývané `CParsedExpression` v tomto příkladu), která spouští `IDebugParsedExpression` rozhraní a ukládá do třídy výraz, který má být analyzován.

3. Vrátí `IDebugParsedExpression` rozhraní z `CParsedExpression` objektu.

> [!NOTE]
> V příkladech, které následují a ve vzorku MyCEE, vyhodnocení výrazu neodděluje analýzu od hodnocení.

## <a name="managed-code"></a>Spravovaný kód
 Následující kód ukazuje implementaci `IDebugExpressionEvaluator::Parse` ve spravovaném kódu. Tato verze metody odkládá analýzu [na EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) jako kód pro analýzu také vyhodnocuje současně (viz [Vyhodnocení watch výraz).](../../extensibility/debugger/evaluating-a-watch-expression.md)

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
Následující kód je implementace `IDebugExpressionEvaluator::Parse` v nespravovaném kódu. Tato metoda volá pomocnou `Parse`funkci , analyzovat výraz a zkontrolovat chyby, ale tato metoda ignoruje výslednou hodnotu. Formální vyhodnocení je odloženo na [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) kde je výraz analyzován, zatímco je vyhodnocován (viz [Vyhodnocení výrazu Watch).](../../extensibility/debugger/evaluating-a-watch-expression.md)

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
- [Vyhodnocení výrazu okna sledování](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Vyhodnocení výrazu Sledování](../../extensibility/debugger/evaluating-a-watch-expression.md)
