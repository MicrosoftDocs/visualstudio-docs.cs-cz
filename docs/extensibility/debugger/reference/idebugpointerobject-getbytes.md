---
title: IDebugPointerObject::GetBytes | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17bc39f65d7c4c42b4f958b559df7c5b7d3bbdf7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725515"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Získá hodnotu ukázal jako řada po sobě jdoucích bajtů.

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
[v] Posun v bajtech od začátku objektu, na který byl odkazován.

`dwCount`\
[v] Počet bajtů načíst.

`pBytes`\
[dovnitř, ven] Pole, které je vyplněno hodnotou jako řada po sobě jdoucích bajtů, počínaje daným posunem od objektu, na který je odkazováno.

`pdwBytes`\
[out] Vrátí počet skutečně načtených bajtů.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda se používá, pokud ukazatel reprezentované tímto [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) odkazuje na primitivní typ nebo jednoduché pole primitivních typů (to znamená pole, které může být reprezentováno jednoduchou sekvencí bajtů).

## <a name="see-also"></a>Viz také
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
