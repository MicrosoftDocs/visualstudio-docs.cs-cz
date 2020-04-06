---
title: IDebugExpressionEvaluator::GetMethodProperty | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ebcf24ee39505091ff79c1f2f31d505217f77efb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729514"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Tato metoda získá objekt vlastnosti, který obsahuje místní, argumenty a další vlastnosti metody.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parametry
`pSymbolProvider`\
[v] Zprostředkovatel symbolu, který má být použit, vyjádřený jako objekt [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[v] Adresa v kódu, vyjádřená jako objekt [IDebugAddress,](../../../extensibility/debugger/reference/idebugaddress.md) která by měla být přeložena na nejbližší obsahující funkci.

`pBinder`\
[v] Pořadač, který má být použit, vyjádřený jako objekt [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`fIncludeHiddenLocals`\
[v] Nenulová`TRUE`( )znamená zahrnout skryté místní obyvatele; nula`FALSE`( ) znamená vynechat skryté místní obyvatele

`ppProperty`\
[out] Vrátí objekt [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) který představuje metodu.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Skryté místní jsou obvykle proměnné, které jsou generovány kompilátorem.

## <a name="see-also"></a>Viz také
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
