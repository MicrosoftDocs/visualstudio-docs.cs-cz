---
description: Tato struktura popisuje místní proměnnou, parametr nebo jiné pole.
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27055178f01f41bb6b4642b8c4d70ea6346b9e74
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059416"
---
# <a name="field_info"></a>FIELD_INFO
Tato struktura popisuje místní proměnnou, parametr nebo jiné pole.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>Členové
`dwFields`\
Kombinace příznaků z výčtu [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) , které určují členy, kteří jsou vyplněni.

`bstrFullName`\
Celé jméno pole

`bstrName`\
Krátký název pole.

`bstrType`\
Typ pole.

`dwModifiers`\
Kombinace příznaků z výčtu [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) , který popisuje pole.

## <a name="remarks"></a>Poznámky
Tato struktura je předána metodě [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) , kde je vyplněna.

## <a name="requirements"></a>Požadavky
Záhlaví: SH. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
