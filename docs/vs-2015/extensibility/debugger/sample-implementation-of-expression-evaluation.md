---
title: Ukázková implementace vyhodnocení výrazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7a19247b296d7e00a15051e75dd53536133c426
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64858566"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Ukázková implementace vyhodnocení výrazu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Pro výraz okna **kukátka** aplikace Visual Studio volá [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) k vytvoření objektu [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpressionContext2::ParseText` Vytvoří instanci vyhodnocovacího filtru výrazů (EE) a zavolá [analýzu](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) , aby získala objekt [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
 Tato implementace `IDebugExpressionEvaluator::Parse` provádí následující úlohy:  
  
1. [Pouze C++] Analyzuje výraz pro hledání chyb.  
  
2. Vytvoří instanci třídy (volanou `CParsedExpression` v tomto příkladu), která implementuje `IDebugParsedExpression` rozhraní a ukládá do třídy výraz, který se má analyzovat.  
  
3. Vrátí `IDebugParsedExpression` rozhraní z `CParsedExpression` objektu.  
  
> [!NOTE]
> V příkladech, které následují a v ukázce mycee, vyhodnocovací filtr výrazů odděluje analýzu od vyhodnocení.  
  
## <a name="managed-code"></a>Spravovaný kód  
 Toto je implementace `IDebugExpressionEvaluator::Parse` ve spravovaném kódu. Všimněte si, že tato verze metody odkládá analýzu na [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , protože kód pro analýzu se také vyhodnocuje současně (viz [vyhodnocení výrazu kukátko](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
 Toto je implementace `IDebugExpressionEvaluator::Parse` v nespravovaném kódu. Tato metoda volá pomocnou funkci, `Parse` , k analýze výrazu a kontrole chyb, ale tato metoda ignoruje výslednou hodnotu. Formální vyhodnocení se odloží na [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , kde se při vyhodnocování výrazu analyzuje (viz [vyhodnocení výrazu kukátka](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```cpp#  
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
 [Vyhodnocení výrazu okna kukátka](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Vyhodnocení výrazu kukátka](../../extensibility/debugger/evaluating-a-watch-expression.md)
