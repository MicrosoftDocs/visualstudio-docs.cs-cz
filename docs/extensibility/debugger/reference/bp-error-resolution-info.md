---
title: BP_ERROR_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48c4bc888db0ad8be6a0d6e98eeea2223a27e8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738082"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Popisuje rozlišení zarážky chyby, včetně umístění, programu a vlákna.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>Členové
`dwFields`\
Kombinace hodnot z výčtu [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) určující, která pole této struktury jsou vyplněna.

`bpResLocation`\
[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) sjednocení, které určuje umístění rozlišení zarážky.

`pProgram`\
Objekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který představuje aplikaci, ve které došlo k chybě zarážky.

`pThread`\
Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , který představuje vlákno, ve kterém je spuštěna aplikace, která generovala chybu zarážky.

`bstrMessage`\
Řetězec obsahující všechna upozornění nebo chybovou zprávu, která vyplývají z tohoto řešení chyb.

`dwType`\
Hodnota z výčtu [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) , která určuje typ chyby zarážky.

## <a name="remarks"></a>Poznámky
Tato struktura je vrácena z metody [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
