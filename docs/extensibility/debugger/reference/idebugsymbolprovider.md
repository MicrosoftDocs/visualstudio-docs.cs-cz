---
description: Toto rozhraní představuje poskytovatele symbolů, který poskytuje symboly a typy a vrací je jako pole.
title: IDebugSymbolProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bda1ec3c65e2f3fdc811b6bde636e78f5a787f32
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053162"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Toto rozhraní představuje poskytovatele symbolů, který poskytuje symboly a typy a vrací je jako pole.

## <a name="syntax"></a>Syntax

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
Zprostředkovatel symbolů musí implementovat toto rozhraní k zadání symbolu a informací o typu do vyhodnocovacího filtru výrazů.

## <a name="notes-for-callers"></a>Poznámky pro volající
Toto rozhraní se získává pomocí funkce modelu COM `CoCreateInstance` (u nespravovaných zprostředkovatelů symbolů) nebo načtením příslušného spravovaného sestavení kódu a vytvořením instance poskytovatele symbolů na základě informací nalezených v tomto sestavení. Modul ladění vytvoří instanci zprostředkovatele symbolů pro fungování v koordinaci s vyhodnocovacím filtrem výrazů. Podívejte se na příklad jednoho přístupu k vytvoření instance tohoto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
V následující tabulce jsou uvedeny metody `IDebugSymbolProvider` .

|Metoda|Popis|
|------------|-----------------|
|`Initialize`|Zastaralé Nepoužívat.|
|`Uninitialize`|Zastaralé Nepoužívat.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Získá pole, které obsahuje adresu pro ladění.|
|`GetField`|Zastaralé Nepoužívat.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Mapuje umístění dokumentu na pole adres ladění.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Mapuje kontext dokumentu na pole adres ladění.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Mapuje adresu pro ladění do kontextu dokumentu.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Získá jazyk používaný ke kompilaci kódu na adrese ladění.|
|`GetGlobalContainer`|Zastaralé Nepoužívat.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Získá pole reprezentující plně kvalifikovaný název metody.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Načte typ pole třídy představující plně kvalifikovaný název třídy.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Vytvoří enumerátor pro obory názvů přidružené k adrese pro ladění.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Mapuje název symbolu na typ symbolu.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Získá adresu pro ladění, která následuje po dané adrese ladění v metodě.|

## <a name="remarks"></a>Poznámky
Toto rozhraní mapuje pozice dokumentu na adresy ladění a naopak.

## <a name="requirements"></a>Požadavky
Záhlaví: SH. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak vytvořit instanci poskytovatele symbolů s ohledem na jeho identifikátor GUID (ladicí stroj musí tuto hodnotu znát).

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
- [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
