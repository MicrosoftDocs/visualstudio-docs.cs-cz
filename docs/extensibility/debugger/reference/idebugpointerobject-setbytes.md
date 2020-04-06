---
title: IDebugPointerObject::SetBytes | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dede3ee5291afbfbeab4d6e60dcbd56e205e4526
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725510"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Nastaví hodnotu, na kterou se ukazuje z řady po sobě jdoucích bajtů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>Parametry
`dwStart`\
[v] Posun v bajtech od začátku objektu, na který byl odkazován.

`dwCount`\
[v] Počet bajtů, které chcete nastavit.

`pBytes`\
[v] Pole bajtů představující novou hodnotu. Tato hodnota je uložena do objektu, počínaje daným posunem.

`pdwBytes`\
[out] Vrátí počet skutečně nastavených bajtů.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda se používá, pokud ukazatel reprezentované tímto [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) odkazuje na primitivní typ nebo jednoduché pole primitivních typů (to znamená pole, které může být reprezentováno jednoduchou sekvencí bajtů). Tento `IDebugPointerObject` objekt nemůže být nulový odkaz (musí odkazovat na adresu v paměti).

## <a name="see-also"></a>Viz také
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
