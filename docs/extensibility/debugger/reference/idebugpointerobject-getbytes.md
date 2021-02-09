---
title: 'IDebugPointerObject:: GetBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1961aaf45478f25ed8eb55d8eda91a5c4eafc4dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852944"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Získá hodnotu, na kterou se odkazuje jako řada po sobě jdoucích bajtů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>Parametry
`dwStart`\
pro Posun v bajtech od začátku objektu, na který ukazuje.

`dwCount`\
pro Počet bajtů, které mají být načteny.

`pBytes`\
[in, out] Pole, které je vyplněno hodnotou jako série po sobě jdoucích bajtů, počínaje daným posunutím od objektu, na který ukazuje.

`pdwBytes`\
mimo Vrátí počet bajtů, které byly skutečně načteny.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda se používá, pokud ukazatel reprezentovaný tímto [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) odkazuje na primitivní typ nebo na jednoduché pole primitivních typů (tj. pole, které lze reprezentovat jednoduchou sekvencí bajtů).

## <a name="see-also"></a>Viz také
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
