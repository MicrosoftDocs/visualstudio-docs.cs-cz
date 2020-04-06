---
title: DEBUG_PROPERTY_INFO | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34fc1b5103949a767a3ee448618cbb708ea6a48b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737447"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
Obsahuje informace o vlastnosti ladění.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagDEBUG_PROPERTY_INFO {
    DEBUGPROP_INFO_FLAGS dwValidFields;
    BSTR                 bstrFullName;
    BSTR                 bstrName;
    BSTR                 bstrType;
    BSTR                 bstrValue;
    IDebugProperty2*     pProperty;
    DBG_ATTRIB_FLAGS     dwAttrib;
} DEBUG_PROPERTY_INFO;
```

```csharp
public struct DEBUG_PROPERTY_INFO {
    public uint            dwValidFields;
    public string          bstrFullName;
    public string          bstrName;
    public string          bstrType;
    public string          bstrValue;
    public IDebugProperty2 pProperty;
    public ulong           dwAttrib;
};
```

## <a name="members"></a>Členové
`dwValidFields`\
Kombinace příznaků z [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) výčtu, která určuje, která pole jsou vyplněna.

`bstrFullName`\
Úplný název vlastnosti.

`bstrName`\
Název vlastnosti v kontextu.

`bstrType`\
Typ vlastnosti jako formátovaný řetězec.

`bstrValue`\
Hodnota vlastnosti jako formátovaný řetězec.

`pProperty`\
[Objekt IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) popsaný touto strukturou.

`dwAttrib`\
Kombinace příznaků z [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) výčtu popisující atributy této vlastnosti.

## <a name="remarks"></a>Poznámky
Vlastnost je objekt hierarchické povahy, který má název, typ a hodnotu. Vlastnost může například popisovat místní proměnné, parametry, sledovat proměnné a výrazy a registry.

Tato struktura je předána [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metoda, kde je vyplněna. Tato struktura je také vrácena jako součást seznamu této struktury z rozhraní [IEnumDebugPropertyInfo2,](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) které je vráceno z volání metod [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) a [EnumProperties.](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
