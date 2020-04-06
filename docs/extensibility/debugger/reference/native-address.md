---
title: NATIVE_ADDRESS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NATIVE_ADDRESS
helpviewer_keywords:
- NATIVE_ADDRESS structure
ms.assetid: 7a0cd085-bfc8-45cc-a3d4-4459070e207a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c62bbea846f3d486ead8add4dfab2182df1e1bb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714332"
---
# <a name="native_address"></a>NATIVE_ADDRESS

Tato struktura představuje nativní adresu.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagNATIVE_ADDRESS {
    DWORD unknown;
} NATIVE_ADDRESS;
```

```csharp
public struct NATIVE_ADDRESS {
    public uint unknown;
}
```

## <a name="members"></a>Členové

`unknown`\
Nativní adresa (význam tohoto závisí na běhu a operačního systému).

## <a name="remarks"></a>Poznámky

Tato struktura je součástí unie ve struktuře [DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) když `dwKind` je pole `DEBUG_ADDRESS_UNION` struktury nastaveno na `ADDRESS_KIND_NATIVE` (hodnota z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) výčtu).

## <a name="requirements"></a>Požadavky

Záhlaví: sh.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také

- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
