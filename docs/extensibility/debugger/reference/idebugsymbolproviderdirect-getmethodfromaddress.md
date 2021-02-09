---
title: 'IDebugSymbolProviderDirect:: GetMethodFromAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3cbcab2126ffa61f4bfb71fbf21abff8ecc5d798
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909435"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Načte informace o metodě na zadané adrese pro ladění.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMethodFromAddress(
   IDebugAddress* pAddress,
   GUID*          pGuid,
   DWORD*         pAppID,
   _mdToken*      pTokenClass,
   _mdToken*      pTokenMethod,
   DWORD*         pdwOffset,
   DWORD*         pdwVersion
);
```

```csharp
int GetMethodFromAddress(
   IDebugAddress pAddress,
   out Guid      pGuid,
   out uint      pAppID,
   out uint      pTokenClass,
   out uint      pTokenMethod,
   out uint      pdwOffset,
   out uint      pdwVersion
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
pro Adresa pro ladění reprezentovaná rozhraním [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)

`pGuid`\
mimo Jedinečný identifikátor modulu

`pAppID`\
mimo Identifikátor domény aplikace

`pTokenClass`\
mimo Token, který reprezentuje třídu obsahující.

`pTokenMethod`\
mimo Token, který představuje modul.

`pdwOffset`\
mimo Posun v bajtech od začátku `pAddress` parametru.

`pdwVersion`\
mimo Číslo verze metody

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
