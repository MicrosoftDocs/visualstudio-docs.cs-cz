---
title: 'IDebugSymbolProvider:: GetTypeByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetTypeByName method
ms.assetid: b9d88d3b-8b75-484a-b9cc-dc8c0fbb4bc8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 565a202d3b63a8c501864099940f5ca16da96077
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894865"
---
# <a name="idebugsymbolprovidergettypebyname"></a>IDebugSymbolProvider::GetTypeByName
Tato metoda mapuje název symbolu na typ symbolu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetTypeByName( 
   LPCOLESTR     pszClassName,
   NAME_MATCH    nameMatch,
   IDebugField** ppField
);
```

```csharp
int GetTypeByName(
   string          pszClassName,
   NAME_MATCH      nameMatch,
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametry
`pszClassName`\
pro Název symbolu.

`nameMatch`\
pro Vybere typ shody, například rozlišování velkých a malých písmen. Hodnota z výčtu [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) .

`ppField`\
mimo Vrátí typ symbolu jako objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je obecná verze [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md).

## <a name="see-also"></a>Viz také
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
- [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)
