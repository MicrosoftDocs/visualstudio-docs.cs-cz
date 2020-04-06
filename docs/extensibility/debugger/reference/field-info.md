---
title: FIELD_INFO | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e2089746adecc583d04176afca18ad19826ea53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736898"
---
# <a name="field_info"></a>FIELD_INFO
Tato struktura popisuje místní proměnnou, parametr nebo jiné pole.

## <a name="syntax"></a>Syntaxe

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
Kombinace příznaků z [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) výčtu, který určuje, které členy jsou vyplněny.

`bstrFullName`\
Úplný název pole.

`bstrName`\
Krátký název pole.

`bstrType`\
Typ pole.

`dwModifiers`\
Kombinace příznaků z [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) výčtu, který popisuje pole.

## <a name="remarks"></a>Poznámky
Tato struktura je předána [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metoda, kde je vyplněna.

## <a name="requirements"></a>Požadavky
Záhlaví: sh.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
