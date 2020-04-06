---
title: BP_REQUEST_INFO | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35a1202f4990f4f6370ad031c896ba85ebb6d816
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737893"
---
# <a name="bp_request_info"></a>BP_REQUEST_INFO
Obsahuje informace potřebné k implementaci zarážky.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_REQUEST_INFO {
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
} BP_REQUEST_INFO;
```

```csharp
public struct BP_REQUEST_INFO {
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

## <a name="remarks"></a>Poznámky
Tato struktura je vrácena [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) metoda.

Pokud potřebujete získat identifikátor GUID dodavatele ladicího motoru, omezení zarážky nebo trasovací bod, podívejte se na [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) strukturu.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
