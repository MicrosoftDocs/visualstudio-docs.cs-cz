---
title: IDebugMemoryBytes2::ReadAt | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f909ac3d2e2993879e4c24140abbf23c2ee8d545
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727532"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Přečte sekvenci bajtů začínajících na daném místě.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

## <a name="parameters"></a>Parametry
`pStartContext`\
[v] [Objekt IDebugMemoryContext2,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) který určuje, kde začít číst bajty.

`dwCount`\
[v] Počet bajtů ke čtení. Také určuje délku `rgbMemory` pole.

`rgbMemory`\
[dovnitř, ven] Pole vyplněno bajty skutečně číst.

`pdwRead`\
[out] Vrátí počet souvislých bajtů skutečně přečtených.

`pdwUnreadable`\
[dovnitř, ven] Vrátí počet nečitelných bajtů. Může být hodnota null, pokud klient nemá zájem o počet nečitelných bajtů.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud jsou požadovány 100 bajtů a prvních 50 jsou čitelné, dalších 20 jsou nečitelné a zbývajících 30 jsou čitelné, tato metoda vrátí:

 *`pdwRead`= 50

 *`pdwUnreadable`= 20

 V tomto případě `*pdwRead + *pdwUnreadable < dwCount`protože volající musí provést další volání číst zbývajících 30 bajtů původní 100 požadované a [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objekt předán v parametru `pStartContext` musí být upřesňována 70.

## <a name="see-also"></a>Viz také
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
