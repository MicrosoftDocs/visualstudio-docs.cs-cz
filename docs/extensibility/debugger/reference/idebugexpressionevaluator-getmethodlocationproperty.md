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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ddc9c17b90be6d65786d58ff2bf585461c4fc69f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092186"
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
