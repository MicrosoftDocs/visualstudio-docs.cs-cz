---
title: BP_CONDITION | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88ed6b6468c5765c8f987c1f15f3e4e8ade9c8c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738102"
---
# <a name="bp_condition"></a>BP_CONDITION
Popisuje podmínky, za kterých je aktivována zarážka.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>Členové
`pThread`\
[Objekt IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) který představuje aktivní vlákno pro aplikaci, která obsahuje zarážku.

`styleCondition`\
Hodnota z [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) výčtu popisující styl této podmínky zarážky.

`bstrContext`\
Umístění zarážky.

`bstrCondition`\
Podmínka spuštění zarážky.

`nRadix`\
Radix, který se použije při vyhodnocování jakýchkoli vyhodnocujících číselné informace.

## <a name="remarks"></a>Poznámky
Tato struktura je členem [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) a [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktur.

Tato struktura je také předána jako parametr metod [setcondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) a [SetCondition.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
