---
description: Určuje, jaké informace se mají načíst o objektu vlastnosti ladění.
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63467e93b80648e6a00728dc66971b7c9b3c9b24
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170520"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Určuje, jaké informace se mají načíst o objektu vlastnosti ladění.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Pole
`DEBUGPROP_INFO_FULLNAME`\
Inicializujte nebo použijte `bstrFullName` pole.

`DEBUGPROP_INFO_NAME`\
Inicializujte nebo použijte `bstrName` pole.

`DEBUGPROP_INFO_TYPE`\
Inicializujte nebo použijte `bstrType` pole.

`DEBUGPROP_INFO_VALUE`\
Inicializujte nebo použijte `bstrValue` pole.

`DEBUGPROP_INFO_ATTRIB`\
Inicializujte nebo použijte `dwAttrib` pole.

`DEBUGPROP_INFO_PROP`\
Inicializujte nebo použijte `pProperty` pole obsahující rozhraní [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Určuje, že pole hodnota by mělo obsahovat automaticky rozbalenou hodnotu, pokud je k dispozici, pro tento typ objektu.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Zastaralé

`DEBUGPROP_INFO_VALUE_RAW`\
Nevracet žádné hodnoty beautified ani členy (tj. Neformátovat hodnoty).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Nevracet žádné speciální syntetizované hodnoty (například Nevolejte `ToString()` na objekt pro vytvoření hodnoty).

`DEBUGPROP_INFO_NONE`\
Určuje, že nejsou nastavené žádné příznaky.

`DEBUGPROP_INFO_STANDARD`\
Inicializujte nebo použijte `dwAttrib` `bstrName` pole,, a `bstrType` `bstrValue` .

`DEBUGPROP_INFO_All`\
Označuje masku všech příznaků.

## <a name="remarks"></a>Poznámky
Tyto hodnoty jsou předány metodám [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)a [enumproperties –](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) , které označují, která pole se mají inicializovat [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury.

Tyto hodnoty jsou také použity pro `dwFields` člena `DEBUG_PROPERTY_INFO` struktury k označení, která pole struktury jsou použita a platná při vrácení struktury.

Tyto hodnoty mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
