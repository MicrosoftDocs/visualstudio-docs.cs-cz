---
title: BPREQI_FIELDS | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737747"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Určuje informace, které mají být načteny o požadavku na zarážku.

## <a name="syntax"></a>Syntaxe

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

## <a name="fields"></a>Fields (Pole)
`BPREQI_BPLOCATION`\
Inicializovat/použít `bpLocation` pole (umístění zarážky) [struktury BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) nebo [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

`BPREQI_LANGUAGE`\
Inicializovat/použít `guidLanguage` pole `BP_REQUEST_INFO` nebo `BP_REQUEST_INFO2` struktury.

`BPREQI_PROGRAM`\
Inicializovat/použít `pProgram` pole `BP_REQUEST_INFO` nebo `BP_REQUEST_INFO2` struktury.

`BPREQI_PROGRAMNAME`\
Inicializovat/použít `bstrProgramName` pole `BP_REQUEST_INFO` nebo `BP_REQUEST_INFO2` struktury.

`BPREQI_THREAD`\
Inicializovat/použít `pThread` pole `BP_REQUEST_INFO` nebo `BP_REQUEST_INFO2` struktury.

`BPREQI_THREADNAME`\
Inicializovat/použít `bstrThreadName` pole `BP_REQUEST_INFO` nebo `BP_REQUEST_INFO2` struktury.

`BPREQI_PASSCOUNT`\
Inicializovat/použít `bpPassCount` pole `BP_REQUEST_INFO` nebo `BP_REQUEST_INFO2` struktury.

`BPREQI_CONDITION`\
Inicializovat/použít `bpCondition` pole (podmínka `BP_REQUEST_INFO` zarážky) `BP_REQUEST_INFO2` nebo struktury.

`BPREQI_FLAGS`\
Inicializovat/použít `dwFlags` pole `BP_REQUEST_INFO` nebo `BP_REQUEST_INFO2` struktury.

`BPREQI_ALLOLDFIELDS`\
Inicializovat/použít všechna pole `BP_REQUEST_INFO` pro strukturu.

`BPREQI_VENDOR`\
Inicializovat/použít `guidVendor` pole `BP_REQUEST_INFO2` struktury.

`BPREQI_CONSTRAINT`\
Inicializovat/použít `bstrConstraint` pole `BP_REQUEST_INFO2` struktury.

`BPREQI_TRACEPOINT`\
Inicializovat/použít `bstrTracepoint` pole `BP_REQUEST_INFO2` struktury.

`BPREQI_ALLFIELDS`\
Určuje všechna pole `BP_REQUEST_INFO2` pro strukturu.

## <a name="remarks"></a>Poznámky
Předánjako argument [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) a [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) metody určit, která pole [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) a [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury mají být inicializovány.

Tyto příznaky se také používají k `BP_REQUEST_INFO` `BP_REQUEST_INFO2` označení, která pole a struktury se používají a jsou platné při vrácení každé struktury.

Tyto hodnoty mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
