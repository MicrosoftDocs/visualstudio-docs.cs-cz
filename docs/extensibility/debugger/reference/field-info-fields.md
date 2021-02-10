---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8cec892d65dc4e5d081063fa6b31def06fb7f85c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936909"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Určuje, jaké informace se mají načíst o objektu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>Pole
`FIF_FULLNAME`\
Inicializujte nebo použijte `bstrFullName` pole ve struktuře [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .

`FIF_NAME`\
Inicializujte nebo použijte `bstrName` pole ve `FIELD_INFO` struktuře.

`FIF_TYPE`\
Inicializujte nebo použijte `bstrType` pole ve `FIELD_INFO` struktuře.

`FIF_MODIFIERS`\
Inicializujte nebo použijte `bstrModifiers` pole ve `FIELD_INFO` struktuře.

## <a name="remarks"></a>Poznámky
Tyto hodnoty jsou také předány jako argument metody [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) , aby bylo možné určit, která pole [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury mají být inicializována.

Tyto hodnoty se používají také v `dwFields` členu `FIELD_INFO` struktury k označení, která pole se používají a jsou platná.

Tyto příznaky mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
Záhlaví: SH. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
