---
title: Ukázková implementace vyhodnocení výrazu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 10efa25ba2f692e9cf4a9c3588d210d31f9e8065
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49901291"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Ukázková implementace vyhodnocení výrazu
> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [vyhodnocovací filtr výrazů spravované ukázka](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Pro **Watch** výrazu okna, volání sady Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) k vytvoření [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objektu. `IDebugExpressionContext2::ParseText` vytvoří instanci vyhodnocovače výrazů (EE) a volání [analyzovat](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zobrazíte [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objektu.  
  
 `IDebugExpressionEvaluator::Parse` Provádí následující úlohy:  
  
1.  [Jenom C++] Analyzuje výrazu vyhledávání chyb.  
  
2.  Vytvoří instanci třídy (volá `CParsedExpression` v tomto příkladu), který běží `IDebugParsedExpression` rozhraní a uloží ve třídě výraz, který má být analyzován.  
  
3.  Vrátí `IDebugParsedExpression` rozhraní z `CParsedExpression` objektu.  
  
> [!NOTE]
>  V následující příklady a ukázkové MyCEE vyhodnocovací filtr výrazů není samostatné analyzování z hodnocení.  
  
## <a name="managed-code"></a>Spravovaný kód  
 Následující kód ukazuje implementaci `IDebugExpressionEvaluator::Parse` ve spravovaném kódu. Tato verze metody odloží analýzy k [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) jako kód pro analýzu také vyhodnotí ve stejnou dobu (naleznete v tématu [vyhodnocení výrazu kukátka](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
Následující kód je implementace `IDebugExpressionEvaluator::Parse` v nespravovaném kódu. Tato metoda volá funkci pomocné rutiny, `Parse`, parsovat výraz a zkontrolujte chyby, ale tato metoda ignoruje výslednou hodnotu. Formální hodnocení je odložena na [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) kde výrazu je analyzován, zatímco je vyhodnocen (viz [vyhodnocení výrazu kukátka](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Vyhodnocení výrazu okna kukátka](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Vyhodnocení výrazu kukátka](../../extensibility/debugger/evaluating-a-watch-expression.md)