---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea493170c7b422129485fcea4248981a2b506001
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713256"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Tato struktura představuje adresu, která `this` je`Me` relativní k ukazateli (v jazyce Visual Basic).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagUNMANAGED_THIS_RELATIVE {
   DWORD dwOffset;
   DWORD dwBitOffset;
   DWORD dwBitLength;
} UNMANAGED_ADDRESS_THIS_RELATIVE;
```

```csharp
public struct UNMANAGED_THIS_RELATIVE {
   public uint dwOffset;
   public uint dwBitOffset;
   public uint dwBitLength;
}
```

## <a name="members"></a>Členové
 `dwOffset`\
 Posun bajtu od základní pozice (například začátek vtable třídy).

 `dwBitOffset`\
 Posun v bitech ze základní polohy (vždy 0, pokud neodkazuje na bitové pole).

 `dwBitLength`\
 Počet bitů představujících adresu (vždy 0, pokud neodkazuje na bitové pole).

## <a name="remarks"></a>Poznámky
 Tato struktura je součástí unie ve struktuře [DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) když `dwKind` je pole `DEBUG_ADDRESS_UNION` struktury nastaveno na `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` (hodnota z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) výčtu).

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
