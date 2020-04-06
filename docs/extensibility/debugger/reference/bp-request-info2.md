---
title: BP_REQUEST_INFO2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04d1db2ca8176678d8a72a84ede2bddcbfa2f152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737876"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Obsahuje informace potřebné k implementaci zarážky, včetně identifikátoru GUID dodavatele, omezení a trasovacího bodu.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_REQUEST_INFO2 {
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
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
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
Kombinace příznaků z [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) výčtu, který určuje, která pole jsou vyplněna.

`guidLanguage`\
Identifikátor GUID jazyka.

`bpLocation`\
[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktury, která určuje typ umístění zarážky.

`pProgram`\
[Objekt IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) který představuje aplikaci, ve které dochází k zarážky.

`bstrProgramName`\
Název aplikace, ve kterém dojde k zarážce.

`pThread`\
[Objekt IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) který představuje vlákno, ve kterém dojde k zarážky.

`bstrThreadName`\
Název vlákna, ve kterém dochází k zarážky.

`bpCondition`\
[BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) struktura, která popisuje podmínky, za kterých bude zarážky požáru.

`bpPassCount`\
[BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) struktura, která obsahuje informace o počtu průchodů zarážky.

`dwFlags`\
Kombinace příznaků z [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) výčtu, který určuje příznaky pro požadovanou zarážku.

`guidVendor`\
IDENTIFIKÁTOR GUID dodavatele. Může být hodnota null.

`bstrConstraint`\
Název omezení zarážky. Může být hodnota null.

`bstrTracepoint`\
Název bodu trasování. Může být hodnota null.

## <a name="remarks"></a>Poznámky
Tato struktura je vrácena [metodou GetRequestInfo2.](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

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
