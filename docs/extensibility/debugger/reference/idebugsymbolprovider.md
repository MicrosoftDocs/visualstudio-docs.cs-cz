---
title: IDebugSymbolProvider | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11e180288a9312d9af5a3d3b1bd63d8f2266f581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719170"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Toto rozhraní představuje zprostředkovatele symbolů, který poskytuje symboly a typy, jejich vrácení jako pole.

## <a name="syntax"></a>Syntaxe

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
Zprostředkovatel symbolu musí implementovat toto rozhraní, aby poskytl symbol a zadá informace hodnotiteli výrazu.

## <a name="notes-for-callers"></a>Poznámky pro volající
Toto rozhraní je získáno `CoCreateInstance` pomocí funkce COM (pro zprostředkovatele nespravovaných symbolů) nebo načtením příslušného sestavení spravovaného kódu a vytvořením instance zprostředkovatele symbolu na základě informací nalezených v tomto sestavení. Ladicí modul inkonsuje zprostředkovatele symbolu pro práci v koordinaci s vyhodnocením výrazu. Viz Příklad pro jeden přístup k vytvoření konkretiončování tohoto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
V následující tabulce jsou `IDebugSymbolProvider`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|`Initialize`|Zastaralé Nepoužívat.|
|`Uninitialize`|Zastaralé Nepoužívat.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Získá pole, které obsahuje ladicí adresu.|
|`GetField`|Zastaralé Nepoužívat.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Mapuje pozici dokumentu do pole ladicích adres.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Mapuje kontext dokumentu do pole ladicích adres.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Mapuje ladicí adresu do kontextu dokumentu.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Získá jazyk používaný ke kompilaci kódu na ladicí adresu.|
|`GetGlobalContainer`|Zastaralé Nepoužívat.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Získá pole představující plně kvalifikovaný název metody.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Získá typ pole třídy představující plně kvalifikovaný název třídy.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Vytvoří čítač pro obory názvů přidružené k ladicí adrese.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Mapuje název symbolu na typ symbolu.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Získá ladicí adresu, která následuje za danou ladicí adresu v metodě.|

## <a name="remarks"></a>Poznámky
Toto rozhraní mapuje pozice dokumentu na ladicí adresy a naopak.

## <a name="requirements"></a>Požadavky
Záhlaví: sh.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak vytvořit instanci zprostředkovatele symbolu, vzhledem k jeho identifikátorgui (ladicí modul musí znát tuto hodnotu).

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
