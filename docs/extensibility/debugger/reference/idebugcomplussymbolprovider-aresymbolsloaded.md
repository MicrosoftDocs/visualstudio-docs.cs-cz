---
description: Určuje, zda jsou pro daný modul načteny symboly ladění s identifikátorem domény aplikace.
title: 'IDebugComPlusSymbolProvider:: AreSymbolsLoaded | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- AreSymbolsLoaded
- IDebugComPlusSymbolProvider::AreSymbolsLoaded
ms.assetid: bbf8707d-f89c-4177-b019-d519f1ec6f4a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 567a0906544a28c2f145e8b4361045b56b6f9278
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088299"
---
# <a name="idebugcomplussymbolprovideraresymbolsloaded"></a>IDebugComPlusSymbolProvider::AreSymbolsLoaded
Určuje, zda jsou pro daný modul načteny symboly ladění s identifikátorem domény aplikace.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT AreSymbolsLoaded (
    ULONG32 ulAppDomainID,
    GUID    guidModule
);
```

```csharp
int AreSymbolsLoaded (
    uint ulAppDomainID,
    Guid guidModule
);
```

## <a name="parameters"></a>Parametry
`ulAppDomainID`\
pro Identifikátor pro doménu aplikace

`guidModule`\
pro Jedinečný identifikátor pro modul

## <a name="return-value"></a>Návratová hodnota
Pokud jsou symboly ladění načteny, vrátí, `S_OK` jinak vrátí `S_FALSE` .

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro objekt **CDebugSymbolProvider** , který zpřístupňuje rozhraní [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .

```cpp
HRESULT CDebugSymbolProvider::AreSymbolsLoaded(
    ULONG32 ulAppDomainID,
    GUID guidModule
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::AreSymbolsLoaded );

    IfFalseGo( GetModule( idModule, &pModule ) == S_OK, S_FALSE );
Error:

    METHOD_EXIT( CDebugSymbolProvider::AreSymbolsLoaded, hr );
    return hr;
}
```

## <a name="see-also"></a>Viz také
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
