---
title: Implementace vlastnosti GetMethodProperty | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 252d09eee9c69ca75cb46d28dde807f2c500737f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738511"
---
# <a name="implement-getmethodproperty"></a>Implementovat vlastnost GetMethodProperty
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio volá ladicí modul (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md), který zase volá [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) získat informace o aktuální metodě v rámci zásobníku.

Tato implementace `IDebugExpressionEvaluator::GetMethodProperty` provádí následující úkoly:

1. Volání [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), předávání v [Objektu IDebugAddress.](../../extensibility/debugger/reference/idebugaddress.md) Zprostředkovatel symbolu (SP) vrátí [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) představující metodu, která obsahuje zadanou adresu.

2. Získá [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) z `IDebugContainerField`.

3. Vytvoří instance třídy (tzv. `CFieldProperty` v tomto příkladu), která implementuje rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) a obsahuje `IDebugMethodField` objekt vrácený z sp.

4. Vrátí `IDebugProperty2` rozhraní z `CFieldProperty` objektu.

## <a name="managed-code"></a>Spravovaný kód
Tento příklad ukazuje `IDebugExpressionEvaluator::GetMethodProperty` implementaci ve spravovaném kódu.

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        public HRESULT GetMethodProperty(
                IDebugSymbolProvider symbolProvider,
                IDebugAddress        address,
                IDebugBinder         binder,
                int                  includeHiddenLocals,
            out IDebugProperty2      property)
        {
            IDebugContainerField containerField = null;
            IDebugMethodField methodField       = null;
            property = null;

            // Get the containing method field.
            symbolProvider.GetContainerField(address, out containerField);
            methodField = (IDebugMethodField) containerField;

            // Return the property of method field.
            property = new CFieldProperty(symbolProvider, address, binder, methodField);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Nespravovaný kód
Tento příklad ukazuje `IDebugExpressionEvaluator::GetMethodProperty` implementaci v nespravovaném kódu.

```
[CPP]
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(
        in IDebugSymbolProvider *pprovider,
        in IDebugAddress        *paddress,
        in IDebugBinder         *pbinder,
        in BOOL                  includeHiddenLocals,
        out IDebugProperty2    **ppproperty
    )
{
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    IDebugContainerField* pcontainer = NULL;

    hr = pprovider->GetContainerField(paddress, &pcontainer);
    if (FAILED(hr))
        return hr;

    IDebugMethodField*    pmethod    = NULL;
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,
            reinterpret_cast<void**>(&pmethod));
    pcontainer->Release();
    if (FAILED(hr))
        return hr;

    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,
                                                         paddress,
                                                         pbinder,
                                                         pmethod );
    pmethod->Release();
    if (!pfieldProperty)
        return E_OUTOFMEMORY;

    hr = pfieldProperty->Init();
    if (FAILED(hr))
    {
        pfieldProperty->Release();
        return hr;
    }

    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,
            reinterpret_cast<void**>(ppproperty));
    pfieldProperty->Release();

    return hr;
}
```

## <a name="see-also"></a>Viz také
- [Ukázková implementace místních obyvatel](../../extensibility/debugger/sample-implementation-of-locals.md)
