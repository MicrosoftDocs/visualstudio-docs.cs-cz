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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47b7c7cb3a77d0ad925b044130901dd481b99943
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162430"
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
