---
title: Vyhodnocení výrazu kukátka | Microsoft Docs
description: Přečtěte si, jak Visual Studio používá EvaluateSync, když je připravený k zobrazení hodnoty výrazu kukátka.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7d7433c9d4c2d5851dc5078a41c33a4391a75d86
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915671"
---
# <a name="evaluate-a-watch-expression"></a>Vyhodnocení výrazu kukátka
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Když je Visual Studio připraveno k zobrazení hodnoty výrazu kukátka, volá [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md), který zase volá [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Tento proces vytvoří objekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , který obsahuje hodnotu a typ výrazu.

V této implementaci `IDebugParsedExpression::EvaluateSync` je výraz analyzován a vyhodnocován ve stejnou dobu. Tato implementace provádí následující úlohy:

1. Analyzuje a vyhodnotí výraz pro vytvoření obecného objektu, který obsahuje hodnotu a typ. V jazyce C# je tato reprezentace vyjádřena jako `object` v jazyce C++, která je znázorněna jako `VARIANT` .

2. Vytvoří instanci třídy (volanou `CValueProperty` v tomto příkladu), která implementuje `IDebugProperty2` rozhraní a ukládá do třídy hodnotu, která se má vrátit.

3. Vrátí `IDebugProperty2` rozhraní z `CValueProperty` objektu.

## <a name="managed-code"></a>Spravovaný kód
Toto je implementace `IDebugParsedExpression::EvaluateSync` ve spravovaném kódu. Pomocná metoda `Tokenize` analyzuje výraz do stromu analýz. Pomocná funkce `EvalToken` převede token na hodnotu. Pomocná funkce `FindTerm` rekurzivně projde stromem analýzy `EvalToken` a volá pro každý uzel, který představuje hodnotu a ve výrazu používá operace (sčítání nebo odčítání).

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
Toto je implementace `IDebugParsedExpression::EvaluateSync` v nespravovaném kódu. Pomocná funkce `Evaluate` analyzuje a vyhodnotí výraz a vrátí z něj `VARIANT` výslednou hodnotu. Pomocná funkce `VariantValueToProperty` Sada `VARIANT` vytvoří `CValueProperty` objekt do objektu.

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
- [Vyhodnotit výraz okna kukátka](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Ukázková implementace vyhodnocení výrazu](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
