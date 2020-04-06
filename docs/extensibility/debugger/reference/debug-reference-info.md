---
title: DEBUG_REFERENCE_INFO | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e31205f52151679f932877c9c4fdc56907ea59e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737413"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
Popisuje odkaz.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>Členové
`dwFields`\
Kombinace příznaků z [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) výčtu, který určuje, která pole jsou vyplněna.

`bstrName`\
Název objektu [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) zadaný uživatelem.

`bstrType`\
Typ odkazu jako formátovaný řetězec.

`bstrValue`\
Referenční hodnota jako formátovaný řetězec

`dwAttrib`\
Kombinace příznaků z [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) výčtu, který určuje příznaky pro atributy vlastnosti ladění.

`dwRefType`\
Hodnota z [výčtu REFERENCE_TYPE,](../../../extensibility/debugger/reference/reference-type.md) který určuje, zda je typ odkazu silný nebo slabý.

`m_pReference`\
Objekt [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) který určuje referenční informace.

## <a name="remarks"></a>Poznámky
Tato struktura je předána volání [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) metoda, která má být vyplněna. Tato struktura je také vrácena jako součást seznamu z rozhraní [IEnumDebugReferenceInfo2,](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) který je zase vrácen z volání [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) metody.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
