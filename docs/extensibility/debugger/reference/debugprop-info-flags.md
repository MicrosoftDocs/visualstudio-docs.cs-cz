---
title: DEBUGPROP_INFO_FLAGS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa7e4a498188dc91f2a47b3ccf27f367f15ec77b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737405"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Určuje, jaké informace se mají načíst o objektu vlastnosti ladění.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>Fields (Pole)
`DEBUGPROP_INFO_FULLNAME`\
Inicializovat/použít `bstrFullName` pole.

`DEBUGPROP_INFO_NAME`\
Inicializovat/použít `bstrName` pole.

`DEBUGPROP_INFO_TYPE`\
Inicializovat/použít `bstrType` pole.

`DEBUGPROP_INFO_VALUE`\
Inicializovat/použít `bstrValue` pole.

`DEBUGPROP_INFO_ATTRIB`\
Inicializovat/použít `dwAttrib` pole.

`DEBUGPROP_INFO_PROP`\
Inicializovat/použít `pProperty` pole, které obsahuje rozhraní [IDebugProperty2.](../../../extensibility/debugger/reference/idebugproperty2.md)

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Určuje, že pole hodnoty by mělo obsahovat hodnotu automatického rozbalení, pokud je k dispozici, pro tento typ objektu.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Zastaralé

`DEBUGPROP_INFO_VALUE_RAW`\
Nevracejte žádné zkrášlené hodnoty nebo členy (to znamená, že hodnoty neformátujte).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Nevracejte žádné speciální syntetizované hodnoty (například nevolejte `ToString()` objekt k vytvoření hodnoty).

`DEBUGPROP_INFO_NONE`\
Určuje, že nejsou nastaveny žádné příznaky.

`DEBUGPROP_INFO_STANDARD`\
Inicializovat/použít `dwAttrib` `bstrName`pole `bstrType`, `bstrValue` , a.

`DEBUGPROP_INFO_All`\
Označuje masku všech příznaků.

## <a name="remarks"></a>Poznámky
Tyto hodnoty jsou předány [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)a [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) metody k označení, která pole mají být inicializována [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury.

Tyto hodnoty se také `dwFields` používají `DEBUG_PROPERTY_INFO` pro člen struktury k označení, která pole struktury se používají a jsou platné při vrácení struktury.

Tyto hodnoty mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
