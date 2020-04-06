---
title: BP_LOCATION_TYPE | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e6bdc0dba8f6bcbdd55c45132dff02735786d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737951"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Určuje typ umístění zarážky pro požadavek zarážky.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="fields"></a>Fields (Pole)
`BPLT_NONE`\
Neurčuje žádné umístění zarážky.

`BPLT_FILE_LINE`\
Určuje typ umístění zarážky jako řádek souboru.

`BPLT_FUNC_OFFSET`\
Určuje typ umístění zarážky jako posun funkce.

`BPLT_CONTEXT`\
Určuje typ umístění zarážky jako kontext.

`BPLT_STRING`\
Určuje typ umístění zarážky jako řetězec.

`BPLT_ADDRESS`\
Určuje typ umístění zarážky jako adresu.

`BPLT_RESOLUTION`\
Určuje typ umístění zarážky jako rozlišení.

`BPLT_CODE_FILE_LINE`\
Určuje typ umístění zarážky jako řádek zdrojového kódu.

`BPLT_CODE_FUNC_OFFSET`\
Určuje typ umístění zarážky jako posun funkce kódu.

`BPLT_CODE_CONTEXT`\
Určuje typ umístění zarážky jako kontext kódu.

`BPLT_CODE_STRING`\
Určuje typ umístění zarážky jako řetězec kódu.

`BPLT_CODE_ADDRESS`\
Určuje typ umístění zarážky jako kódovou adresu.

`BPLT_DATA_STRING`\
Určuje typ umístění zarážky jako datový řetězec.

`BPLT_TYPE_MASK`\
Určuje bitovou masku, aby bylo možné extrahovat typ zarážky z hodnoty.

`BPLT_LOCATION_TYPE_MASK`\
Určuje bitovou masku, aby bylo možné extrahovat typ umístění zarážky z hodnoty.

## <a name="remarks"></a>Poznámky
Předánjako parametr metodě [GetLocationType.](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)

Typ umístění zarážky se skládá z typu zarážky a typu umístění. To znamená, že typ umístění zarážky není nikdy pouze `BPT_CODE`typ zarážky (například) nebo typ umístění `BPLT_FILE_LINE`(například). Do tohoto výčtu`BPLT_CODE_FILE_LINE` (prostřednictvím) `BPLT_DATA_STRING`jsou zahrnuty předdefinované konstanty pro všechny aktuálně podporované typy umístění zarážky.

`BPT_CODE`a `BPT_DATA` jsou členy [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) výčtu.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
