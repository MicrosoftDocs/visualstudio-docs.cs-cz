---
title: IDebugMemoryBytes2::WriteAt | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac9113424c6cd5cce230774a6e5335ffa4d4ba77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727527"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Zapíše zadaný počet bajtů paměti počínaje zadanou adresou.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>Parametry
`pStartContext`\
[v] Objekt [IDebugMemoryContext2,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) který určuje, kde začít psát bajty.

`dwCount`\
[v] Počet bajtů zapsat.

`rgbMemory`\
[v] Bajtů psát. Předpokládá se, že toto pole má velikost alespoň `dwCount` bajtů.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném `S_FALSE` případě vrátí, pokud ne všechny bajty mohou `E_FAIL`být zapsány nebo vrátí kód chyby (obvykle).

## <a name="remarks"></a>Poznámky
 Pokud počáteční adresa není v okně paměti reprezentované tento objekt [IDebugMemoryBytes2,](../../../extensibility/debugger/reference/idebugmemorybytes2.md) dojde k žádné zápisu a `E_FAIL` je vrácen kód chyby – i v případě, že částka zápisu překrývá do paměťového prostoru.

## <a name="see-also"></a>Viz také
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
