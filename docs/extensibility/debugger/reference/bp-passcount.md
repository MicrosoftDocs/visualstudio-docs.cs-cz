---
title: BP_PASSCOUNT | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e3177ff093aea9a6f52465bd606b22883249d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737910"
---
# <a name="bp_passcount"></a>BP_PASSCOUNT
Popisuje počet a podmínky, za kterých je aktivována podmíněná zarážka.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_PASSCOUNT {
    DWORD              dwPassCount;
    BP_PASSCOUNT_STYLE stylePassCount;
} BP_PASSCOUNT;
```

```csharp
public struct BP_PASSCOUNT {
    public uint dwPassCount;
    public uint stylePassCount;
};
```

## <a name="members"></a>Členové
`dwPassCount`\
Počet, kolikrát předat zarážku před jeho spuštěním.

`stylePassCount`\
Hodnota z [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) výčtu, který určuje styl počet průchodu zarážky.

## <a name="remarks"></a>Poznámky
Tato struktura je členem [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktury.

Tato struktura je také předána jako parametr metod[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) a[SetPassCount.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)
- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
