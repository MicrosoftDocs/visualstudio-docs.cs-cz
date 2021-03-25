---
description: Tato struktura představuje adresu.
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b250654f45f18adcfd9c52a6047b2b8798be75b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096366"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
Tato struktura představuje adresu.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagDEBUG_ADDRESS {
    ULONG32             ulAppDomainID;
    GUID                guidModule;
    _mdToken            tokClass;
    DEBUG_ADDRESS_UNION addr;
} DEBUG_ADDRESS;
```

```csharp
public struct DEBUG_ADDRESS {
    public uint                ulAppDomainID;
    public Guid                guidModule;
    public int                 tokClass;
    public DEBUG_ADDRESS_UNION addr;
}
```

## <a name="members"></a>Členové
`ulAppDomainID`\
ID procesu.

`guidModule`\
Identifikátor GUID modulu, který obsahuje tuto adresu.

`tokClass`\
Token identifikující třídu nebo typ této adresy.

> [!NOTE]
> Tato hodnota je specifická pro poskytovatele symbolů, proto nemá žádný obecný význam, než jako identifikátor typu třídy.

`addr`\
Struktura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , která obsahuje sjednocení struktur popisujících jednotlivé typy adres. Hodnota `addr` .`dwKind` pochází z výčtu [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , který vysvětluje, jak se má sjednocení interpretovat.

## <a name="remarks"></a>Poznámky
Tato struktura je předána metodě [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) , která má být vyplněna.

**Upozornění [pouze C++]**

Pokud `addr.dwKind` je `ADDRESS_KIND_METADATA_LOCAL` a pokud není `addr.addr.addrLocal.pLocal` hodnota null, musíte zavolat `Release` na ukazatel tokenu:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Požadavky
Záhlaví: SH. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
