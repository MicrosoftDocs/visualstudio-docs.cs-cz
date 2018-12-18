---
title: IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetAttributedClassesForLanguage
- IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage
ms.assetid: e5b1b8b6-52a6-4ade-9a36-644abfa9f4b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 78d62fd8627f9397f3d14668ffc963e10a28abd0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913368"
---
# <a name="idebugcomplussymbolprovidergetattributedclassesforlanguage"></a>IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage
Načte tříd, které jsou implementovány v zadané programovací jazyk pomocí zadaného atributu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[C++]  
HRESULT GetAttributedClassesForLanguage (  
   GUID               guidLanguage,  
   LPOLESTR           pstrAttribute,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```  
[C#]  
int GetAttributedClassesForLanguage (  
   Guid                 guidLanguage,  
   string               pstrAttribute,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidLanguage`  
 [in] Jedinečný identifikátor jazyka.  
  
 `pstrAttribute`  
 [in] Atribut řetězců.  
  
 `ppEnum`  
 [out] Vrátí výčet tříd atributů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pro tuto metodu implementovat **CDebugSymbolProvider** objekt, který zveřejňuje [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) rozhraní.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetAttributedClassesForLanguage(  
    GUID guidLanguage,  
    __in_z LPOLESTR pstrAttribute,  
    IEnumDebugFields** ppEnum  
)  
{  
    HRESULT hr = S_OK;  
    CFieldList listFields;  
    CModIter ModIter;  
    CModule* pModule; // the iterator owns the reference  
    ULONG cClasses = 0;  
    DWORD iTypeDef = 0;  
    mdTypeDef* rgTypeDefs = NULL;  
    IDebugField** rgFields = NULL;  
    DWORD ctField = 0;  
    CEnumDebugFields* pEnumFields = NULL;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppEnum, IEnumDebugFields*));  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetAttributedClassesForLanguage );  
  
    IfFalseGo( ppEnum, E_INVALIDARG );  
    *ppEnum = NULL;  
  
    // For Each Module - call EnumFields  
    IfFailGo( GetModuleIter(&ModIter) );  
  
    // Find the Max number of classes  
    while (ModIter.GetNext(&pModule))  
    {  
        CComPtr<IMetaDataImport> pMetaData;  
        HCORENUM hEnum = 0;  
        ULONG cTypeDefs;  
        ULONG cEnum;  
  
        pModule->GetMetaData( &pMetaData );  
  
        IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                           NULL,  
                                           0,  
                                           &cTypeDefs ) );  
        IfFailGo( pMetaData->CountEnum( hEnum, &cEnum ) );  
        cClasses += cEnum;  
    }  
  
    IfNullGo( rgTypeDefs = new mdTypeDef[cClasses], E_OUTOFMEMORY );  
    IfNullGo( rgFields = new IDebugField * [cClasses], E_OUTOFMEMORY );  
  
    ModIter.Reset();  
  
    // Create the classes  
    while (ModIter.GetNext(&pModule))  
    {  
        CComPtr<IMetaDataImport> pMetaData;  
        HCORENUM hEnum = 0;  
        ULONG cTypeDefs;  
        ULONG cEnum;  
        const void* pUnused;  
        ULONG cbUnused;  
  
        pModule->GetMetaData( &pMetaData );  
  
        IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                           NULL,  
                                           0,  
                                           &cTypeDefs ) );  
        IfFailGo( pMetaData->CountEnum( hEnum, &cEnum ) );  
        IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                           rgTypeDefs,  
                                           cEnum,  
                                           &cTypeDefs ) );  
  
        pMetaData->CloseEnum(hEnum);  
        hEnum = NULL;  
  
        for ( iTypeDef = 0; iTypeDef < cTypeDefs; iTypeDef++)  
        {  
  
            if (pMetaData->GetCustomAttributeByName( rgTypeDefs[iTypeDef],  
                    pstrAttribute,  
                    &pUnused,  
                    &cbUnused ) == S_OK)  
            {  
                // Only return classes implemeted in the correct language  
  
                if (pModule->ClassImplementedInLanguage( rgTypeDefs[iTypeDef],  
                        guidLanguage) )  
                {  
                    if (CreateClassType( pModule->GetID(),  
                                         rgTypeDefs[iTypeDef],  
                                         rgFields + ctField) == S_OK)  
                    {  
                        ctField++;  
                    }  
                    else  
                    {  
                        ASSERT(!"Failed to Create Attributed Class");  
                    }  
                }  
            }  
        }  
    }  
  
    IfNullGo( pEnumFields = new CEnumDebugFields, E_OUTOFMEMORY );  
    IfFailGo( pEnumFields->Initialize(rgFields, ctField) );  
    IfFailGo( pEnumFields->QueryInterface( __uuidof(IEnumDebugFields),  
                                           (void**) ppEnum ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetAttributedClassesForLanguage, hr );  
  
    DELETERG( rgTypeDefs );  
  
    for ( iTypeDef = 0; iTypeDef < ctField; iTypeDef++)  
    {  
        RELEASE( rgFields[iTypeDef] );  
    }  
  
    DELETERG( rgFields );  
    RELEASE( pEnumFields );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)