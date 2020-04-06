---
title: METADATA_ADDRESS_METHOD | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc3dd7a34e4f9a3e1b933781aeaf4e18cad7ec17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714458"
---
# <a name="metadata_address_method"></a>METADATA_ADDRESS_METHOD
Tato struktura představuje adresu metody třídy.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagMETADATA_ADDRESS_METHOD {
   _mdToken tokMethod;
   DWORD    dwOffset;
   DWORD    dwVersion;
} METADATA_ADDRESS_METHOD;
```

```csharp
public struct METADATA_ADDRESS_METHOD {
   public int  tokMethod;
   public uint dwOffset;
   public uint dwVersion;
}
```

## <a name="members"></a>Členové
 `tokMethod`\
 ID metody.

 [C++] `_mdToken` je `typedef` pro 32bitový `int`.

 `dwOffset`\
 Posun od začátku třídy k této metodě (může představovat posun do vtable).

 `dwVersion`\
 Verze metody (tato hodnota je jedinečná pro zprostředkovatele symbolů).

## <a name="remarks"></a>Poznámky
 Tato struktura je součástí unie ve struktuře [DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) když `dwKind` je pole `DEBUG_ADDRESS_UNION` struktury nastaveno na `ADDRESS_KIND_METHOD` (hodnota z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) výčtu).

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
