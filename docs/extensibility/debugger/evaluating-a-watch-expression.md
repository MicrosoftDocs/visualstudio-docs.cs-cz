---
title: Vyhodnocení výrazu sledování | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a239e430338e88a0be4bc35ad1c357925f7d8f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738852"
---
# <a name="evaluate-a-watch-expression"></a>Vyhodnocení výrazu sledování
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Když visual studio je připraven k zobrazení hodnoty výrazu sledování, volá [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md), což zase volá [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Tento proces vytvoří objekt [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) který obsahuje hodnotu a typ výrazu.

V této `IDebugParsedExpression::EvaluateSync`implementaci aplikace je výraz analyzován a vyhodnocován současně. Tato implementace provádí následující úkoly:

1. Analyzuje a vyhodnocuje výraz k vytvoření obecného objektu, který obsahuje hodnotu a její typ. V jazyce C#, `object` to je reprezentován jako while `VARIANT`v jazyce C++, to je reprezentován jako .

2. Konitekátuje `CValueProperty` třídu (volanou `IDebugProperty2` v tomto příkladu), která implementuje rozhraní a ukládá do třídy hodnotu, která má být vrácena.

3. Vrátí `IDebugProperty2` rozhraní z `CValueProperty` objektu.

## <a name="managed-code"></a>Spravovaný kód
Toto je implementace `IDebugParsedExpression::EvaluateSync` ve spravovaném kódu. Pomocná metoda `Tokenize` analyzuje výraz do stromu analýzy. Pomocná funkce `EvalToken` převede token na hodnotu. Pomocná funkce `FindTerm` rekurzivně prochází stromem analýzy, volá `EvalToken` pro každý uzel představující hodnotu a použití všech operací (sčítání nebo odčítání) ve výrazu.

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT EvaluateSync(
            uint evalFlags,
            uint timeout,
            IDebugSymbolProvider provider,
            IDebugAddress address,
            IDebugBinder binder,
            string resultType,
            out IDebugProperty2 result)
        {
            HRESULT retval = COM.S_OK;
            this.evalFlags = evalFlags;
            this.timeout = timeout;
            this.provider = provider;
            this.address = address;
            this.binder = binder;
            this.resultType = resultType;

            try
            {
                IDebugField field = null;
                // Tokenize, then parse.
                tokens = Tokenize(expression);
                result = new CValueProperty(
                        expression,
                        (int) FindTerm(EvalToken(tokens[0], out field),1),
                        field,
                        binder);
            }
            catch (ParseException)
            {
                result = new CValueProperty(expression, "Huh?");
                retval = COM.E_INVALIDARG;
            }
            return retval;
        }
    }
}
```

## <a name="unmanaged-code"></a>Nespravovaný kód
Toto je implementace `IDebugParsedExpression::EvaluateSync` v nespravovaném kódu. Pomocná funkce `Evaluate` analyzuje a vyhodnocuje `VARIANT` výraz a vrací podržení výsledné hodnoty. Pomocná funkce `VariantValueToProperty` sváže `VARIANT` do `CValueProperty` objektu.

```cpp
STDMETHODIMP CParsedExpression::EvaluateSync(
    in  DWORD                 evalFlags,
    in  DWORD                 dwTimeout,
    in  IDebugSymbolProvider* pprovider,
    in  IDebugAddress*        paddress,
    in  IDebugBinder*         pbinder,
    in  BSTR                  bstrResultType,
    out IDebugProperty2**     ppproperty )
{
    // dwTimeout parameter is ignored in this implementation.
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (paddress == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    VARIANT value;
    BSTR    bstrErrorMessage = NULL;
    hr = ::Evaluate( pprovider,
                     paddress,
                     pbinder,
                     m_expr,
                     &bstrErrorMessage,
                     &value );
    if (hr != S_OK)
    {
        if (bstrErrorMessage == NULL)
            return hr;

        //we can display better messages ourselves.
        HRESULT hrLocal = S_OK;
        VARIANT varType;
        VARIANT varErrorMessage;

        VariantInit( &varType );
        VariantInit( &varErrorMessage );
        varErrorMessage.vt      = VT_BSTR;
        varErrorMessage.bstrVal = bstrErrorMessage;

        CValueProperty* valueProperty = new CValueProperty();
        if (valueProperty != NULL)
        {
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);
            if (SUCCEEDED(hrLocal))
            {
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,
                        reinterpret_cast<void**>(ppproperty) );
            }
        }

        VariantClear(&varType);
        VariantClear(&varErrorMessage); //frees BSTR
        if (!valueProperty)
            return hr;
        valueProperty->Release();
        if (FAILED(hrLocal))
            return hr;
    }
    else
    {
        if (bstrErrorMessage != NULL)
            SysFreeString(bstrErrorMessage);

        hr = VariantValueToProperty( pprovider,
                                     paddress,
                                     pbinder,
                                     m_radix,
                                     m_expr,
                                     value,
                                     ppproperty );
        VariantClear(&value);
        if (FAILED(hr))
            return hr;
    }

    return S_OK;
}
```

## <a name="see-also"></a>Viz také
- [Vyhodnocení výrazu okna kukátka](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Ukázková implementace vyhodnocení exprese](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
