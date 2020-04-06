---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6ba87d6c1a1f7370ce5e209440589f362b87035
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729517"
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
[v] Umístění metody a posun, vyjádřené jako řetězec.

`pSymbolProvider`\
[v] Zprostředkovatel symbolu vyjádřený jako objekt [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[v] Adresa v rámci metody, vyjádřené jako objekt [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

`pBinder`\
[v] Pořadač vyjádřený jako objekt [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`ppProperty`\
[out] Vrátí rozhraní [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) které představuje adresu paměti.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Vrácená adresa slouží například k nastavení zarážky.

 Navzdory názvu `upstrFullyQualifiedMethodPlusOffset`může být tento parametr předán částečně kvalifikovaný název metody. V takovém případě je vybraná metoda, `pAddress`která obklopuje . Způsob interpretace tohoto parametru je na implementaci vyhodnocení výrazu a jazyk, který podporuje.

## <a name="see-also"></a>Viz také
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
