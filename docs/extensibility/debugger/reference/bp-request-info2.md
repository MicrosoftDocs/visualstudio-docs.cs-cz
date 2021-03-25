---
description: Obsahuje informace potřebné k implementaci zarážky, včetně identifikátoru GUID, omezení a zarážka s trasováním dodavatele.
title: BP_REQUEST_INFO2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54ab1ec2ad37517a7a7fbfd7059022e1c5a26f82
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078198"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Obsahuje informace potřebné k implementaci zarážky, včetně identifikátoru GUID, omezení a zarážka s trasováním dodavatele.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_REQUEST_INFO2 {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
    GUID            guidVendor;
    BSTR            bstrConstraint;
    BSTR            bstrTracepoint;
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
    public Guid           guidVendor;
    public string         bstrConstraint;
    public string         bstrTracepoint;
};
```

## <a name="members"></a>Členové
`dwFields`\
Kombinace příznaků z výčtu [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) , která určuje, která pole jsou vyplněna.

`guidLanguage`\
Identifikátor GUID jazyka

`bpLocation`\
Struktura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) , která určuje typ umístění zarážky.

`pProgram`\
Objekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který představuje aplikaci, ve které dojde k zarážce.

`bstrProgramName`\
Název aplikace, ve které dojde k zarážce.

`pThread`\
Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , který představuje vlákno, ve kterém se nachází zarážka.

`bstrThreadName`\
Název vlákna, ve kterém dojde k zarážce.

`bpCondition`\
Struktura [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) , která popisuje podmínky, za kterých se zarážka aktivuje.

`bpPassCount`\
Struktura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) , která obsahuje informace o počtu průchodů zarážky.

`dwFlags`\
Kombinace příznaků z výčtu [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) , které určují příznaky pro požadovanou zarážku.

`guidVendor`\
Identifikátor GUID dodavatele Může být hodnota null.

`bstrConstraint`\
Název omezení zarážky Může být hodnota null.

`bstrTracepoint`\
Název trasovacího bodu. Může být hodnota null.

## <a name="remarks"></a>Poznámky
Tato struktura je vrácena metodou [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
