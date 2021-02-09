---
title: BP_REQUEST_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c806687b9948be693ca25868aaf7211d9ccf6b97
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902022"
---
# <a name="bp_request_info"></a>BP_REQUEST_INFO
Obsahuje informace potřebné k implementaci zarážky.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_REQUEST_INFO {
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
} BP_REQUEST_INFO;
```

```csharp
public struct BP_REQUEST_INFO {
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

## <a name="remarks"></a>Poznámky
Tato struktura je vrácena metodou [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) .

Pokud potřebujete získat GUID ladicího stroje, omezení zarážky nebo zarážka s trasováním, přečtěte si část [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

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
