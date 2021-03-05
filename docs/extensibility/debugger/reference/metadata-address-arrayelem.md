---
description: Tato struktura představuje prvek pole v rámci pole.
title: METADATA_ADDRESS_ARRAYELEM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b7573caf0fee3d3389a212cb9f4012178642e23
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223989"
---
# <a name="metadata_address_arrayelem"></a>METADATA_ADDRESS_ARRAYELEM

Tato struktura představuje prvek pole v rámci pole.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {
    _mdToken tokMethod;
    DWORD    dwIndex;
} METADATA_ADDRESS_ARRAYELEM;
```

```csharp
public struct METADATA_ADDRESS_ARRAYELEM {
    public int  tokMethod;
    public uint dwIndex;
}
```

## <a name="members"></a>Členové

`tokMethod`\
ID pole, jehož součástí je tento prvek.

[C++] `_mdToken` je a `typedef` pro 32-bit `int` .

`dwIndex`\
Index tohoto prvku v poli.

## <a name="remarks"></a>Poznámky
Tato struktura je součástí sjednocení ve struktuře [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , když `dwKind` `DEBUG_ADDRESS_UNION` je pole struktury nastaveno na `ADDRESS_KIND_ARRAYELEM` (hodnota z výčtu [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Požadavky
Záhlaví: SH. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také

- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
