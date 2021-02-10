---
title: 'IDebugParsedExpression:: EvaluateSync | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ff14c10f5563053ce704982455eee6d9dc81b742
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953250"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Tato metoda vyhodnocuje analyzovaný výraz a volitelně přetypování výsledku na jiný datový typ.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EvaluateSync( 
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BSTR                  bstrResultType,
   IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   string               bstrResultType,
   out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Parametry
`dwEvalFlags`\
pro Kombinace [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) konstant, která určuje, jak má být výraz vyhodnocen.

`dwTimeout`\
pro Určuje maximální dobu v milisekundách, po kterou se má čekat, než se vrátí z této metody. Použijte `INFINITE` k čekání na neomezenou dobu.

`pSymbolProvider`\
pro Zprostředkovatel symbolů vyjádřený jako rozhraní [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
pro Aktuální umístění spuštění v rámci metody vyjádřené jako rozhraní [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pBinder`\
pro Pořadač, vyjádřený jako rozhraní [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`bstrResultType`\
pro Typ, na který má být výsledek převeden. Tento argument může být hodnota null.

`ppResult`\
mimo Vrátí rozhraní [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , které představuje výsledky vyhodnocení.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Kontext vyhodnocení výrazu je dán nástrojem `pAddress` , který umožňuje určit obsahující metodu a potom použít pravidla oboru jazyka k určení hodnoty symbolů ve výrazu.

## <a name="see-also"></a>Viz také
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
