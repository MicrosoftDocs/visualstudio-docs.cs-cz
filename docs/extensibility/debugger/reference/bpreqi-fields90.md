---
title: BPREQI_FIELDS90 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea46939118ec48490280d6a85cc84e144d320d4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737731"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Vyjmenová v hodnotě platných hodnot, které určují informace, které mají být načteny o požadavku na zarážku. Tento výčet rozšiřuje [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

## <a name="fields"></a>Fields (Pole)
`BPREQI90_BPLOCATION`\
Inicializovat nebo `bpLocation` použít pole (umístění zarážky) [struktury BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) nebo [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

`BPREQI90_LANGUAGE`\
Inicializovat nebo `guidLanguage` použít `BP_REQUEST_INFO` pole `BP_REQUEST_INFO2` nebo struktury.

`BPREQI90_PROGRAM`\
Inicializovat nebo `pProgram` použít `BP_REQUEST_INFO` pole `BP_REQUEST_INFO2` nebo struktury.

`BPREQI90_PROGRAMNAME`\
Inicializovat nebo `bstrProgramName` použít `BP_REQUEST_INFO` pole `BP_REQUEST_INFO2` nebo struktury.

`BPREQI90_THREAD`\
Inicializovat nebo `pThread` použít `BP_REQUEST_INFO` pole `BP_REQUEST_INFO2` nebo struktury.

`BPREQI90_THREADNAME`\
Inicializovat nebo `bstrThreadName` použít `BP_REQUEST_INFO` pole `BP_REQUEST_INFO2` nebo struktury.

`BPREQI90_PASSCOUNT`\
Inicializovat nebo `bpPassCount` použít `BP_REQUEST_INFO` pole `BP_REQUEST_INFO2` nebo struktury.

`BPREQI90_CONDITION`\
Inicializovat nebo `bpCondition` použít pole (podmínka `BP_REQUEST_INFO` zarážky) nebo struktury nebo. `BP_REQUEST_INFO2`

`BPREQI90_FLAGS`\
Inicializovat nebo `dwFlags` použít `BP_REQUEST_INFO` pole `BP_REQUEST_INFO2` nebo struktury.

`BPREQI90_ALLOLDFIELDS`\
Inicializovat nebo použít všechna `BP_REQUEST_INFO` pole pro strukturu.

`BPREQI90_VENDOR`\
Inicializovat nebo `guidVendor` použít `BP_REQUEST_INFO2` pole struktury.

`BPREQI90_CONSTRAINT`\
Inicializovat nebo `bstrConstraint` použít `BP_REQUEST_INFO2` pole struktury.

`BPREQI90_TRACEPOINT`\
Inicializovat nebo `bstrTracepoint` použít `BP_REQUEST_INFO2` pole struktury.

`BPREQI90_MACROTRACEPOINT`\
Inicializovat nebo `bstrMacroTracepoint` použít `BP_REQUEST_INFO2` pole struktury. BPREQI_ALLFIELDS toto pole nezahrnuje.

`BPREQI90_ALLFIELDS`\
Určuje všechna pole `BP_REQUEST_INFO2` pro strukturu.

## <a name="requirements"></a>Požadavky
Záhlaví: Msdbg90.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
