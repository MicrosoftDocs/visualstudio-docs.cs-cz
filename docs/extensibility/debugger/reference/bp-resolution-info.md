---
description: Popisuje informace o vázané zarážce buď pro zarážku kódu, nebo pro datovou zarážku.
title: BP_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c611b37003df7d8ccab787a14402e64ee2da9ad3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054670"
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
