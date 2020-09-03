---
title: 'IDebugComPlusSymbolProvider2:: LoadSymbolsWithCorModule | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::LoadSymbolsWithCorModule
- LoadSymbolsWithCorModule
ms.assetid: b6abf3a4-ce60-4e66-9637-82ce911148de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef4750de223b133e30e620f5dc0eec526e98526d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733312"
---
# <a name="idebugcomplussymbolprovider2loadsymbolswithcormodule"></a>IDebugComPlusSymbolProvider2::LoadSymbolsWithCorModule
Načte symboly ladění pro daný objekt **ICorDebugModule** .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT LoadSymbolsWithCorModule(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONGLONG baseAddress,
    IUnknown* pUnkMetadataImport,
    IUnknown* pUnkCorDebugModule,
    BSTR      bstrModuleName,
    BSTR      bstrSymSearchPath
);
```

```csharp
int LoadSymbolsWithCorModule(
    uint   ulAppDomainID,
    Guid   guidModule,
    ulong  baseAddress,
    object pUnkMetadataImport,
    object pUnkCorDebugModule,
    string bstrModuleName,
    string bstrSymSearchPath
);
```

## <a name="parameters"></a>Parametry
`ulAppDomainID`\
pro Identifikátor domény aplikace

`guidModule`\
pro Jedinečný identifikátor modulu

`baseAddress`\
pro Základní adresa paměti.

`pUnkMetadataImport`\
pro Objekt, který obsahuje metadata symbolu ladění.

`pUnkCorDebugModule`\
pro Objekt, který implementuje [rozhraní ICorDebugModule](/dotnet/framework/unmanaged-api/debugging/icordebugmodule-interface).

`bstrModuleName`\
pro Název modulu

`bstrSymSearchPath`\
pro Cesta pro vyhledání souboru symbolů

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro objekt **CDebugSymbolProvider** , který zpřístupňuje rozhraní [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) .

```cpp
HRESULT CDebugSymbolProvider::LoadSymbolsWithCorModule(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONGLONG baseOffset,
    IUnknown* _pMetadata,
    IUnknown* _pCorModule,
    BSTR bstrModule,
    BSTR bstrSearchPath)
{
    EMIT_TICK_COUNT("Entry -- Loading symbols for the following target:");
    USES_CONVERSION;
    EmitTickCount(W2A(bstrModule));

    CAutoLock Lock(this);

    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;
    CComPtr<ICorDebugModule> pCorModule;

    CModule* pmodule = NULL;
    CModule* pmoduleNew = NULL;
    bool fAlreadyLoaded = false;
    Module_ID idModule(ulAppDomainID, guidModule);
    bool fSymbolsLoaded = false;
    DWORD dwCurrentState = 0;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(_pMetadata, IUnknown));

    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );

    IfFalseGo( _pMetadata, E_INVALIDARG );
    IfFalseGo( _pCorModule, E_INVALIDARG );

    IfFailGo( _pMetadata->QueryInterface( IID_IMetaDataImport,
                                          (void**)&pMetadata) );

    IfFailGo( _pCorModule->QueryInterface( IID_ICorDebugModule,
                                           (void**)&pCorModule) );

    ASSERT(guidModule != GUID_NULL);

    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;

    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );

    //
    // We are now allowing modules to be created that do not have SymReaders.
    // It is likely there are a number of corner cases being ignored
    // that will require knowledge of the hr result below.
    //
    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;

    HRESULT hrLoad = pmoduleNew->Create( idModule,
                                         dwCurrentState,
                                         pMetadata,
                                         pCorModule,
                                         bstrModule,
                                         bstrSearchPath,
                                         baseOffset );

    if (hrLoad == S_OK)
    {
        fSymbolsLoaded = true;
    }

    // Remove the old module
    if (fAlreadyLoaded)
    {
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));
        RemoveModule( pmodule );
    }

    IfFailGo( AddModule( pmoduleNew ) );

Error:

    RELEASE (pmodule);
    RELEASE (pmoduleNew);

    if (SUCCEEDED(hr) && !fSymbolsLoaded)
    {
        hr = hrLoad;
    }

    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );
    EMIT_TICK_COUNT("Exit");
    return hr;
}
```

## <a name="see-also"></a>Viz také
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
