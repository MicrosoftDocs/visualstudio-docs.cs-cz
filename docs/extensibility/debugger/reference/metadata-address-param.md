---
description: Tato struktura představuje parametr metody nebo funkce.
title: METADATA_ADDRESS_PARAM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_PARAM
helpviewer_keywords:
- METADATA_ADDRESS_PARAM structure
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0171fd59ec034c2015843732cdd361228166e74f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057920"
---
# <a name="metadata_address_param"></a>METADATA_ADDRESS_PARAM
Tato struktura představuje parametr metody nebo funkce.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagMETADATA_ADDRESS_PARAM {
   _mdToken tokMethod;
   _mdToken tokParam;
   DWORD    dwIndex;
} METADATA_ADDRESS_PARAM;
```

```csharp
public struct METADATA_ADDRESS_PARAM {
   public int  tokMethod;
   public int  tokParam;
   public uint dwIndex;
}
```

## <a name="members"></a>Členové
 `tokMethod`\
 ID metody, jejíž parametr je součástí.

 `tokParam`\
 ID parametru

 `dwIndex`\
 Index parametru v seznamu parametrů.

## <a name="remarks"></a>Poznámky
 Tato struktura je součástí sjednocení ve struktuře [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , když `dwKind` `DEBUG_ADDRESS_UNION` je pole struktury nastaveno na `ADDRESS_KIND_PARAM` (hodnota z výčtu [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
