---
description: Načte omezení, která jsou přidružena k tomuto obecnému parametru.
title: 'IDebugGenericParamField:: getomezení | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetConstraints
- GetConstraints
ms.assetid: 86a78b5a-ee0f-4999-a0ba-919d3dc7d969
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80a148907c8bb3a50d41c58777efaf965872a0b4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072738"
---
# <a name="idebuggenericparamfieldgetconstraints"></a>IDebugGenericParamField::GetConstraints
Načte omezení, která jsou přidružena k tomuto obecnému parametru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetConstraints(
    ULONG32       cConstraints,
    IDebugField** ppConstraints,
    ULONG32*      pcConstraints
);
```

```csharp
int GetConstraints(
    uint              cConstraints,
    out IDebugField[] ppConstraints,
    ref uint          pcConstraints
);
```

## <a name="parameters"></a>Parametry
`cConstraints`\
pro Počet omezení.

`ppConstraints`\
mimo Vrátí pole obsahující omezení spojená s tímto polem.

`pcConstraints`\
[in, out] Počet omezení v poli `ppConstraints` .

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro objekt **CDebugGenericParamFieldType** , který zpřístupňuje rozhraní [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) .

```cpp
HRESULT CDebugGenericParamFieldType::GetConstraints(
    ULONG32 cConstraints,
    IDebugField** ppConstraints,
    ULONG32* pcConstraints)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;
    CComPtr<IMetaDataImport2> pMetadata2;
    mdGenericParamConstraint* rgParamConsts = NULL;
    HCORENUM hEnum = 0;
    ULONG cConst = 0;
    ULONG iConst;
    ULONG iConstOut = 0;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetConstraints );

    IfFalseGo(ppConstraints && pcConstraints, E_INVALIDARG );
    *pcConstraints = 0;

    IfNullGo( rgParamConsts = new mdGenericParamConstraint[cConstraints], E_OUTOFMEMORY);

    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );
    IfFailGo( pMetadata->QueryInterface(IID_IMetaDataImport2, (void**)&pMetadata2) );
    IfFailGo( pMetadata2->EnumGenericParamConstraints( &hEnum,
              m_tokParam,
              rgParamConsts,
              cConstraints,
              &cConst) );
    pMetadata->CloseEnum(hEnum);
    hEnum = NULL;

    for (iConst = 0; iConst < cConst; iConst++)
    {
        mdToken tokConst;

        IfFailGo( pMetadata2->GetGenericParamConstraintProps( rgParamConsts[iConst],
                  NULL,
                  &tokConst ) );
        switch (TypeFromToken(tokConst))
        {
            case mdtTypeRef:
                {
                    Module_ID mid;
                    mdTypeDef tokClass;

                    IfFailGo( CDebugClassFieldType::GetClassToken(m_spSH, m_idModule, tokConst, &mid, &tokClass) );
                    IfFailGo( m_spSH->CreateClassType( mid, tokClass, ppConstraints + iConstOut ) );
                    iConstOut++;
                    break;
                }
            case mdtTypeDef:
                {
                    IfFailGo( m_spSH->CreateClassType( m_idModule, tokConst, ppConstraints + iConstOut ) );
                    iConstOut++;
                    break;
                }
            case mdtTypeSpec:
                {
                    PCCOR_SIGNATURE pvSig;
                    ULONG cbSig;
                    DWORD cb = 0;
                    DWORD dwElementType;

                    IfFailGo( pMetadata2->GetTypeSpecFromToken( tokConst, &pvSig, &cbSig) );

                    cb += CorSigUncompressData(&(pvSig[cb]), &dwElementType);

                    IfFailGo( m_spSH->CreateType( pvSig, cbSig, m_idModule, mdMethodDefNil, m_pGenScope, ppConstraints + iConstOut ) );

                    iConstOut++;

                    break;
                }
            default:
                {
                    ASSERT(!"Bad constraint token");
                }
        }
    }

    *pcConstraints = iConstOut;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetConstraints, hr );

    DELETERG(rgParamConsts);

    return hr;
}
```

## <a name="see-also"></a>Viz také
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
