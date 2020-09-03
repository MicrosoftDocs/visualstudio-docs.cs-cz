---
title: BPREQI_FIELDS90 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737731"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Vytvoří výčet platných hodnot, které určují informace, které mají být načteny o požadavku na zarážku. Tento výčet rozšiřuje výčet [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) .

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Pole
`BPREQI90_BPLOCATION`\
Inicializujte nebo použijte `bpLocation` pole (umístění zarážky) struktury [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) nebo [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

`BPREQI90_LANGUAGE`\
Inicializujte nebo použijte `guidLanguage` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI90_PROGRAM`\
Inicializujte nebo použijte `pProgram` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI90_PROGRAMNAME`\
Inicializujte nebo použijte `bstrProgramName` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI90_THREAD`\
Inicializujte nebo použijte `pThread` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI90_THREADNAME`\
Inicializujte nebo použijte `bstrThreadName` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI90_PASSCOUNT`\
Inicializujte nebo použijte `bpPassCount` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI90_CONDITION`\
Inicializujte nebo použijte `bpCondition` pole (Podmínka zarážky) `BP_REQUEST_INFO` struktury nebo `BP_REQUEST_INFO2` .

`BPREQI90_FLAGS`\
Inicializujte nebo použijte `dwFlags` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI90_ALLOLDFIELDS`\
Inicializujte nebo použijte všechna pole pro `BP_REQUEST_INFO` strukturu.

`BPREQI90_VENDOR`\
Inicializujte nebo použijte `guidVendor` pole `BP_REQUEST_INFO2` struktury.

`BPREQI90_CONSTRAINT`\
Inicializujte nebo použijte `bstrConstraint` pole `BP_REQUEST_INFO2` struktury.

`BPREQI90_TRACEPOINT`\
Inicializujte nebo použijte `bstrTracepoint` pole `BP_REQUEST_INFO2` struktury.

`BPREQI90_MACROTRACEPOINT`\
Inicializujte nebo použijte `bstrMacroTracepoint` pole `BP_REQUEST_INFO2` struktury. BPREQI_ALLFIELDS toto pole neobsahuje.

`BPREQI90_ALLFIELDS`\
Určuje všechna pole pro `BP_REQUEST_INFO2` strukturu.

## <a name="requirements"></a>Požadavky
Záhlaví: Msdbg90. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
