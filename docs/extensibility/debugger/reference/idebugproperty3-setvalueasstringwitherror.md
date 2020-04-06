---
title: IDebugProperty3::SetValueAsStringWithError | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::SetValueAsStringWithError
helpviewer_keywords:
- IDebugProperty3::SetValueAsStringWithError
ms.assetid: b378368f-4a45-4b2f-8e3d-3bff7a18ab17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb3441dabba1ff13600a9e505eeaec5ae93acd8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721076"
---
# <a name="idebugproperty3setvalueasstringwitherror"></a>IDebugProperty3::SetValueAsStringWithError
Nastaví hodnotu této vlastnosti a v případě potřeby vrátí chybovou zprávu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetValueAsStringWithError(
    LPCOLESTR pszValue,
    DWORD     dwRadix,
    DWORD     dwTimeout,
    BSTR*     errorString
);
```

```csharp
int SetValueAsStringWithError(
    string     pszValue,
    uint       dwRadix,
    uint       dwTimeout,
    out string errorString
);
```

## <a name="parameters"></a>Parametry
`pszValue`\
[v] Hodnota nastavena.

`dwRadix`\
[v] Radix nastavené hodnoty.

`dwTimeout`\
[v] Doba čekání na hodnotu, která má`INFINITE` být nastavena (znamená čekat navždy).

`errorString`\
[out] Pokud došlo k chybě nastavení hodnoty, to platí důvod selhání.

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Příchozí hodnota může být výraz, který má být vyhodnocen.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro **cproperty** objekt, který zveřejňuje rozhraní [IDebugProperty3.](../../../extensibility/debugger/reference/idebugproperty3.md)

```cpp
HRESULT CProperty::SetValueAsStringWithError(
    LPCOLESTR in_szValue,
    DWORD in_RADIX,
    DWORD in_TIMEOUT,
    BSTR * out_ERRORTEXT
)
{
    // precondition
    REQUIRE( NULL != in_szValue );

    if (NULL == in_szValue)
        return E_INVALIDARG;

    INVARIANT( this );
    if (!this->ClassInvariant())
        return E_UNEXPECTED;

    if (NULL == m_pPropertyContext->m_pCEE->m_LanguageSpecificUseCases.pfSetValue)
        return S_OK;

    // function body
    DEBUG_PROPERTY_INFO dpInfo,dpInfo2;
    HRESULT HR = this->GetPropertyInfo(DEBUGPROP_INFO_FULLNAME | DEBUGPROP_INFO_ATTRIB | DEBUGPROP_INFO_TYPE | DEBUGPROP_INFO_VALUE_AUTOEXPAND,
                                       in_RADIX,
                                       in_TIMEOUT,
                                       NULL,
                                       0,
                                       &dpInfo);

    if (ENSURE( S_OK == HR ))
    {
        REQUIRE( NULL != dpInfo.bstrFullName );
        REQUIRE( NULL != dpInfo.bstrType );

        REQUIRE( NULL == dpInfo.bstrName );
        REQUIRE( NULL == dpInfo.bstrValue );
        REQUIRE( NULL == dpInfo.pProperty );

        BSTR bstrError = NULL;

        UINT ichError = 0;
        IDebugProperty2* pProperty = NULL;
        IDebugParsedExpression* pParsedExpression = NULL;

        CComBSTR bstrValue = dpInfo.bstrFullName;
        bstrValue += L" = ";
        bstrValue += in_szValue;
        HR = this->m_pPropertyContext->m_pCEE->
                Parse(bstrValue, 0, in_RADIX, &bstrError, &ichError, &pParsedExpression);
        if (S_OK == HR)
        {
            REQUIRE( NULL == bstrError );
            HR = pParsedExpression->EvaluateSync(EVAL_NOEVENTS | EVAL_RETURNVALUE,
                                                 in_TIMEOUT,
                                                 m_pPropertyContext->m_pSymbolProvider,
                                                 m_pPropertyContext->m_pAddress,
                                                 m_pPropertyContext->m_pBinder,
                                                 NULL,
                                                 &pProperty);

            dpInfo2.dwAttrib = DBG_ATTRIB_VALUE_ERROR;
            if (pProperty)
            {
                pProperty->GetPropertyInfo(DEBUGPROP_INFO_ATTRIB | DEBUGPROP_INFO_VALUE,10,in_TIMEOUT,NULL,0,&dpInfo2);
            }
            if (DBG_ATTRIB_VALUE_ERROR & dpInfo2.dwAttrib)
            {
                HR = E_FAIL;
                bstrError = dpInfo2.bstrValue;
            }
            else
            {
                ::SysFreeString(dpInfo.bstrValue);
            }
            EXTERNAL_RELEASE(pProperty);
            EXTERNAL_RELEASE(pParsedExpression);
        }

        if (bstrError)
        {
            if(out_ERRORTEXT)
            {
                *out_ERRORTEXT = bstrError;
                bstrError = NULL;
            }
            else
            {
                ::SysFreeString(bstrError);
            }
        }
        ::SysFreeString(dpInfo.bstrFullName);
        ::SysFreeString(dpInfo.bstrType);
    }

    // postcondition
    INVARIANT( this );

    return HR;
}
```

## <a name="see-also"></a>Viz také
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
