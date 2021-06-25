---
title: Získání místních vlastností | Microsoft Docs
description: Zjistěte, Visual Studio s těmito příklady pro spravovaný a nespravovaný kód používá vlastnost EnumWeather k získání místních vlastností.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c45933c6340836fac889f1309c14a71feed31791
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900730"
---
# <a name="get-local-properties"></a>Získání místních vlastností
> [!IMPORTANT]
> V Visual Studio 2015 je tento způsob implementace vyhodnocovače výrazů zastaralý. Informace o implementaci vyhodnocovačů výrazů CLR najdete v tématu Vyhodnocovače [výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovače spravovaných výrazů](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio [volá objekt Enum Přemísteč,](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) aby získal [objekt IEnumDebugPropertyInfo2,](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) který poskytuje přístup ke všem místním hodnotům, které se mají zobrazit v **okně Místních** hodnot. Visual Studio pak zavolá [metodu Next,](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) aby se informace pro jednotlivé místní prostředí zobrazovány. V tomto příkladu `CEnumPropertyInfo` třída implementuje rozhraní `IEnumDebugPropertyInfo2` .

Tato implementace `IEnumDebugPropertyInfo2::Next` provádí následující úlohy:

1. Vymaže pole, ve kterém se informace uloží.

2. Zavolá [metodu Next](../../extensibility/debugger/reference/ienumdebugfields-next.md) pro každou místní DEBUG_PROPERTY_INFO [vrácené](../../extensibility/debugger/reference/debug-property-info.md) hodnoty do pole, které se má vrátit. Objekt [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) byl zadán při vytvoření `CEnumPropertyInfo` instance této třídy.

## <a name="managed-code"></a>Spravovaný kód
Tento příklad ukazuje implementaci pro místní hodnoty metody ve `IEnumDebugPropertyInfo2::EnumChildren` spravovaném kódu.

```csharp
namespace EEMC
{
    public class CEnumMethodField : IEnumDebugFields
    {
        public HRESULT Next(
                uint                  count,
                DEBUG_PROPERTY_INFO[] properties,
            out uint                  fetched)
        {
            if (count > properties.Length)
                throw new COMException();

            // Zero out the array.
            for (int i= 0; i < count; i++)
            {
                properties[i].bstrFullName = "";
                properties[i].bstrName = "";
                properties[i].bstrType = "";
                properties[i].bstrValue = "";
                properties[i].dwAttrib = 0;
                properties[i].dwFields = 0;
                properties[i].pProperty = null;
            }
            fetched = 0;

            // COM interop.
            HRESULT hr;
            uint innerFetched;
            IDebugField[] field = new IDebugField[1];

            while (fetched < count)
            {
                field[0] = null;
                innerFetched = 0;

                // Get next field.
                if (fetched < fieldCount)
                    hr = fields.Next(1, field, ref innerFetched);
                // No more fields.
                else return COM.S_FALSE;

                if (hr != COM.S_OK || innerFetched != 1 || field[0] == null)
                    throw new COMException("CEnumPropertyInfo.Next");

                // Get property from field.
                CFieldProperty fieldProperty =
                        new CFieldProperty(provider, address, binder, field[0]);

                DEBUG_PROPERTY_INFO[] property =
                        new DEBUG_PROPERTY_INFO[1];
                fieldProperty.GetPropertyInfo((uint) infoFlags, radix, 0, null, 0, property);
                properties[fetched++] = property[0];
            }
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Nespravovaný kód
 Tento příklad ukazuje implementaci pro místní hodnoty metody v `IEnumDebugPropertyInfo2::EnumChildren` nespravovaném kódu.

```cpp
STDMETHODIMP CEnumPropertyInfo::Next(
    in  ULONG                count,
    out DEBUG_PROPERTY_INFO* pelements,
    out ULONG*               pfetched )
{
    if (pfetched)
        *pfetched = 0;
    if (!pelements)
        return E_INVALIDARG;
    else
        memset( pelements, 0, count * sizeof(DEBUG_PROPERTY_INFO));

    HRESULT hr  = S_OK;
    ULONG   idx = 0;
    while (idx < count)
    {
        ULONG        fetchedFields;
        IDebugField* pfield;

        //get the next field
        hr = m_fields->Next( 1, &pfield, &fetchedFields );
        if (FAILED(hr))
            return hr;
        if (fetchedFields != 1)
            return E_FAIL;
        idx++;

        //create a CFieldProperty to retrieve the DEBUG_PROPERTY_INFO
        CFieldProperty* pproperty =
            new CFieldProperty( m_provider, m_address, m_binder, pfield );
        pfield->Release();
        if (!pproperty)
            return E_OUTOFMEMORY;

        hr = pproperty->Init();
        if (FAILED(hr))
        {
            pproperty->Release();
            return hr;
        }

        hr = pproperty->GetPropertyInfo( m_infoFlags,
                                         m_radix,
                                         0,
                                         NULL,
                                         0,
                                         pelements + idx - 1);
        pproperty->Release();
        if (FAILED(hr))
            return hr;
    }

    if (pfetched)
        *pfetched = idx;
    return hr;
}
```

## <a name="see-also"></a>Viz také
- [Ukázková implementace místních hodnoty](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Vytváření výčtu místních hodnot](../../extensibility/debugger/enumerating-locals.md)
