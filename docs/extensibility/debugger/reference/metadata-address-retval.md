---
title: METADATA_ADDRESS_RETVAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2437d10078eb623e063b3292d96ef9bb4a9cf64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714278"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
Tato struktura představuje návratovou hodnotu z metody nebo funkce.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>Členové
 `tokMethod`\
 ID metody, pro kterou se tato návratová hodnota používá

 `dwCorType`\
 Základní typ návratové hodnoty. Toto je hodnota z `CorElementType` výčtu definovaného v souboru .NET Framework SDK corhdr. h.

 `dwSigSize`\
 Velikost signatury návratové hodnoty (jak je uložená v `rgSig` ).

 `rgSig`\
 Pole bajtů tvořících podpis návratové hodnoty.

## <a name="remarks"></a>Poznámky
 Tato struktura je součástí sjednocení ve struktuře [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , když `dwKind` `DEBUG_ADDRESS_UNION` je pole struktury nastaveno na `ADDRESS_KIND_RETVAL` (hodnota z výčtu [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
