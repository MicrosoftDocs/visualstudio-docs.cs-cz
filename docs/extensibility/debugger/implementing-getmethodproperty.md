---
title: Implementace GetMethodProperty | Microsoft Docs
description: Přečtěte si, jak Visual Studio získává informace o aktuální metodě v bloku zásobníku pomocí GetDebugProperty – ladicího stroje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c0a52174e05d7203d5bc35e43df8886e23ea7296
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059821"
---
# <a name="implement-getmethodproperty"></a>Implementovat GetMethodProperty
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Sada Visual Studio volá [GetDebugProperty –](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)ladicího stroje (de), který zase volá [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) , aby získala informace o aktuální metodě v bloku zásobníku.

Tato implementace `IDebugExpressionEvaluator::GetMethodProperty` provádí následující úlohy:

1. Volá [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), která předává objekt [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) . Zprostředkovatel symbolů (SP) vrátí [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) představující metodu, která obsahuje zadanou adresu.

2. Získá [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) z `IDebugContainerField` .

3. Vytvoří instanci třídy (volána `CFieldProperty` v tomto příkladu), která implementuje rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) a obsahuje `IDebugMethodField` objekt vrácený z SP.

4. Vrátí `IDebugProperty2` rozhraní z `CFieldProperty` objektu.

## <a name="managed-code"></a>Spravovaný kód
Tento příklad ukazuje implementaci `IDebugExpressionEvaluator::GetMethodProperty` ve spravovaném kódu.

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
Tento příklad ukazuje implementaci `IDebugExpressionEvaluator::GetMethodProperty` v nespravovaném kódu.

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
- [Ukázková implementace místních hodnot](../../extensibility/debugger/sample-implementation-of-locals.md)
