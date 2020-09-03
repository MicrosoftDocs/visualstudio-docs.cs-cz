---
title: BP_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70e66a936ec1eaf1f818ad249aa4eb14b0b63749
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737822"
---
# <a name="bp_resolution_info"></a>BP_RESOLUTION_INFO
Popisuje informace o vázané zarážce buď pro zarážku kódu, nebo pro datovou zarážku.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_RESOLUTION_INFO {
    BPRESI_FIELDS          dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
} BP_RESOLUTION_INFO;
```

```csharp
public struct BP_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
};
```

## <a name="members"></a>Členové
`dwFields`\
Kolekce příznaků z výčtů [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) , které určují, která pole jsou vyplněna.

`bpResLocation`\
Struktura [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) , která určuje umístění zarážky v kódu nebo datech.

`pProgram`\
Objekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který představuje aplikaci, ve které došlo k chybě zarážky.

`pThread`\
Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , který představuje vlákno, ve kterém je spuštěná aplikace, která obsahuje chybu zarážky.

## <a name="remarks"></a>Poznámky
Tato struktura je vrácena pomocí [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md).

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
