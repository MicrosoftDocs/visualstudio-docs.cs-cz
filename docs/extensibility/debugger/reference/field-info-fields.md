---
title: FIELD_INFO_FIELDS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a3d2e796d37606c51918d8e49db920161d63f55
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736905"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Určuje, jaké informace se mají načíst o objektu [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_FIELD_INFO_FIELDS { 
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

## <a name="fields"></a>Fields (Pole)
`FIF_FULLNAME`\
Inicializovat/použít `bstrFullName` pole ve [struktuře FIELD_INFO.](../../../extensibility/debugger/reference/field-info.md)

`FIF_NAME`\
Inicializovat/použít `bstrName` pole `FIELD_INFO` ve struktuře.

`FIF_TYPE`\
Inicializovat/použít `bstrType` pole `FIELD_INFO` ve struktuře.

`FIF_MODIFIERS`\
Inicializovat/použít `bstrModifiers` pole `FIELD_INFO` ve struktuře.

## <a name="remarks"></a>Poznámky
Tyto hodnoty jsou také předány jako argument [getinfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metoda určit, která pole [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury mají být inicializovány.

Tyto hodnoty se také `dwFields` používají `FIELD_INFO` v člen struktury k označení, která pole se používají a jsou platná.

Tyto příznaky mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
Záhlaví: sh.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
