---
description: Tato struktura představuje adresu místní proměnné v rámci oboru (obvykle funkce nebo metody).
title: METADATA_ADDRESS_LOCAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c265f8312b9a23b3b10f06595240dae20894f001
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061547"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL

Tato struktura představuje adresu místní proměnné v rámci oboru (obvykle funkce nebo metody).

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagMETADATA_ADDRESS_LOCAL {
    _mdToken  tokMethod;
    IUnknown* pLocal;
    DWORD     dwIndex;
} METADATA_ADDRESS_LOCAL;
```

```csharp
public struct METADATA_ADDRESS_LOCAL {
    public int    tokMethod;
    public object pLocal;
    public uint   dwIndex;
}
```

## <a name="members"></a>Členové

`tokMethod`\
ID metody nebo funkce, která je místní proměnnou součástí.

[C++] `_mdToken` je a `typedef` pro 32-bit `int` .

`pLocal`\
Token, jehož adresa Tato struktura představuje.

`dwIndex`\
Může být indexem této místní proměnné v metodě nebo funkci nebo v nějaké jiné hodnotě (specifické pro jazyk).

## <a name="remarks"></a>Poznámky

Tato struktura je součástí sjednocení ve struktuře [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , když `dwKind` `DEBUG_ADDRESS_UNION` je pole struktury nastaveno na `ADDRESS_KIND_LOCAL` (hodnota z výčtu [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

> [!WARNING]
> [Pouze C++] Pokud hodnota `pLocal` není null, je nutné volat `Release` ukazatel na token ( `addr` je pole ve struktuře [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) ):
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>Požadavky

Záhlaví: SH. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také

- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
