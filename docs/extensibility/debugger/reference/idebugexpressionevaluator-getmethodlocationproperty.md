---
description: Tato metoda převede umístění metody a posun na adresu paměti.
title: 'IDebugExpressionEvaluator:: GetMethodLocationProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f841f602064b21035ea409457c708f99ec25bf12
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152517"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Tato metoda převede umístění metody a posun na adresu paměti.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parametry
`upstrFullyQualifiedMethodPlusOffset`\
pro Umístění a posunutí metody vyjádřené jako řetězec.

`pSymbolProvider`\
pro Zprostředkovatel symbolů vyjádřený jako objekt [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
pro Adresa v rámci metody vyjádřená jako objekt [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pBinder`\
pro Pořadač vyjádřený jako objekt [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)

`ppProperty`\
mimo Vrátí rozhraní [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , které představuje adresu paměti.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Vrácenou adresu lze použít například k nastavení zarážky.

 Bez ohledu na název `upstrFullyQualifiedMethodPlusOffset` je možné tento parametr předat částečně kvalifikovaný název metody. V takovém případě je vybraná metoda ten, který je ohraničen `pAddress` . Způsob interpretace tohoto parametru je až do implementace vyhodnocovacího filtru výrazů a jazyka, který podporuje.

## <a name="see-also"></a>Viz také
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
