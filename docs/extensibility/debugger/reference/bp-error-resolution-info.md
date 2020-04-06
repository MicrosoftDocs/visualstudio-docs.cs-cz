---
title: BP_ERROR_RESOLUTION_INFO | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738082"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Popisuje řešení zarážky chyby, včetně umístění, programu a vlákna.

## <a name="syntax"></a>Syntaxe

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
Kombinace hodnot z [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) výčtu určující, která pole této struktury jsou vyplněna.

`bpResLocation`\
BP_RESOLUTION_LOCATION [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) unie, která určuje umístění rozlišení zarážky.

`pProgram`\
[Objekt IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) který představuje aplikaci, ve které došlo k chybě zarážky.

`pThread`\
Objekt [IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) který představuje vlákno, na kterém je spuštěna aplikace, která generovala chybu zarážky.

`bstrMessage`\
Řetězec obsahující upozornění nebo chybovou zprávu vyplývající z tohoto řešení chyb.

`dwType`\
Hodnota z [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) výčtu, který určuje typ chyby zarážky.

## <a name="remarks"></a>Poznámky
Tato struktura je vrácena z [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metoda.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
