---
description: Nastaví hodnotu, na kterou se odkazuje z řady po sobě jdoucích bajtů.
title: 'IDebugPointerObject:: SetBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 31feb63e4f9d246161ced3483f487b2877ee5e1e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169662"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Nastaví hodnotu, na kterou se odkazuje z řady po sobě jdoucích bajtů.

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
pro Posun v bajtech od začátku objektu, na který ukazuje.

`dwCount`\
pro Počet bajtů, které se mají nastavit.

`pBytes`\
pro Pole bajtů představující novou hodnotu. Tato hodnota je uložena do objektu, počínaje daným posunutím.

`pdwBytes`\
mimo Vrátí počet aktuálně nastavených bajtů.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda se používá, pokud ukazatel reprezentovaný tímto [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) odkazuje na primitivní typ nebo na jednoduché pole primitivních typů (tj. pole, které lze reprezentovat jednoduchou sekvencí bajtů). Tento `IDebugPointerObject` objekt nemůže být nulovým odkazem (musí odkazovat na adresu v paměti).

## <a name="see-also"></a>Viz také
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
