---
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c0e10b6c253c61a9e68e0cf161201f7d2520ae6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737747"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Určuje informace, které mají být načteny o požadavku na zarážku.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="fields"></a>Pole
`BPREQI_BPLOCATION`\
Inicializujte nebo použijte `bpLocation` pole (umístění zarážky) struktury [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) nebo [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

`BPREQI_LANGUAGE`\
Inicializujte nebo použijte `guidLanguage` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI_PROGRAM`\
Inicializujte nebo použijte `pProgram` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI_PROGRAMNAME`\
Inicializujte nebo použijte `bstrProgramName` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI_THREAD`\
Inicializujte nebo použijte `pThread` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI_THREADNAME`\
Inicializujte nebo použijte `bstrThreadName` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI_PASSCOUNT`\
Inicializujte nebo použijte `bpPassCount` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI_CONDITION`\
Inicializujte nebo použijte `bpCondition` pole (Podmínka zarážky) `BP_REQUEST_INFO` struktury nebo `BP_REQUEST_INFO2` .

`BPREQI_FLAGS`\
Inicializujte nebo použijte `dwFlags` pole `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury nebo.

`BPREQI_ALLOLDFIELDS`\
Inicializujte nebo použijte všechna pole pro `BP_REQUEST_INFO` strukturu.

`BPREQI_VENDOR`\
Inicializujte nebo použijte `guidVendor` pole `BP_REQUEST_INFO2` struktury.

`BPREQI_CONSTRAINT`\
Inicializujte nebo použijte `bstrConstraint` pole `BP_REQUEST_INFO2` struktury.

`BPREQI_TRACEPOINT`\
Inicializujte nebo použijte `bstrTracepoint` pole `BP_REQUEST_INFO2` struktury.

`BPREQI_ALLFIELDS`\
Určuje všechna pole pro `BP_REQUEST_INFO2` strukturu.

## <a name="remarks"></a>Poznámky
Předána jako argument metodám [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) a [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) k určení, která pole [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) a [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury mají být inicializovány.

Tyto příznaky slouží také k označení toho, která pole `BP_REQUEST_INFO` struktury a `BP_REQUEST_INFO2` jsou použita a platná při vrácení každé struktury.

Tyto hodnoty mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
