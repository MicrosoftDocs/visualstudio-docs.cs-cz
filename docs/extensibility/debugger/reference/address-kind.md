---
title: ADDRESS_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1298df79bbe34b240d6e7b186f42e20b3d1a89de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738159"
---
# <a name="address_kind"></a>ADDRESS_KIND
Určuje typy adres.

## <a name="syntax"></a>Syntax

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>Pole
`ADDRESS_KIND_NATIVE`\
Nativní adresa reprezentovaná [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) strukturou.

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
Nespravovaná adresa relativní vzhledem `this` k `Me` ukazateli (v Visual Basic) a reprezentovaná [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) strukturou.

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
Nespravovaná fyzická adresa reprezentovaná [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) strukturou.

`ADDRESS_KIND_METHOD`\
Metoda třídy reprezentovaná [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) strukturou.

`ADDRESS_KIND_FIELD`\
Pole třídy reprezentované [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) strukturou.

`ADDRESS_KIND_LOCAL`\
Adresa je určena pro místní proměnnou a je reprezentována [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) strukturou.

`ADDRESS_KIND_PARAM`\
Metoda nebo parametr funkce reprezentovaný [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) strukturou.

`ADDRESS_KIND_ARRAYELEM`\
Prvek pole reprezentovaný [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) strukturou.

`ADDRESS_KIND_RETVAL`\
Návratová hodnota reprezentovaná [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) strukturou.

## <a name="remarks"></a>Poznámky
Metoda [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) vrátí strukturu [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) , která obsahuje sjednocení možných struktur, struktury [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) . `dwKind`Pole `DEBUG_ADDRESS_UNION` struktury obsahuje `ADDRESS_KIND` hodnotu a popisuje, jak interpretovat pole Union.

## <a name="requirements"></a>Požadavky
Záhlaví: SH. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
