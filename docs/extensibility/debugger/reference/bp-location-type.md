---
description: Určuje typ umístění zarážky pro požadavek na zarážku.
title: BP_LOCATION_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7bb3ea3220c6b4be74e0767f0e88ab1b46d2685c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096704"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Určuje typ umístění zarážky pro požadavek na zarážku.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Pole
`BPLT_NONE`\
Neurčuje umístění zarážky.

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
Určuje typ umístění zarážky jako posunu funkce kódu.

`BPLT_CODE_CONTEXT`\
Určuje typ umístění zarážky jako kontext kódu.

`BPLT_CODE_STRING`\
Určuje typ umístění zarážky jako řetězec kódu.

`BPLT_CODE_ADDRESS`\
Určuje typ umístění zarážky jako kódových adres.

`BPLT_DATA_STRING`\
Určuje typ umístění zarážky jako Datový řetězec.

`BPLT_TYPE_MASK`\
Určuje bitovou masku, aby bylo možné extrahovat typ zarážky z hodnoty.

`BPLT_LOCATION_TYPE_MASK`\
Určuje bitovou masku, aby bylo možné extrahovat typ umístění zarážky mimo hodnotu.

## <a name="remarks"></a>Poznámky
Předán jako parametr metodě [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) .

Typ umístění zarážky se skládá z typu zarážky a typu umístění. To znamená, že typ umístění zarážky nikdy není pouze typ zarážky (například `BPT_CODE` ) nebo typ umístění (například `BPLT_FILE_LINE` ). Předdefinované konstanty pro všechny typy umístění zarážek, které jsou aktuálně podporovány, jsou zahrnuty do tohoto výčtu ( `BPLT_CODE_FILE_LINE` prostřednictvím `BPLT_DATA_STRING` ).

`BPT_CODE` a `BPT_DATA` jsou členy [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) výčtu.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
