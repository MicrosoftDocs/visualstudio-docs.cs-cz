---
title: BP_LOCATION_DATA_STRING | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 75f881feaaa2068abd98d771a63024f20435d98f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737969"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Používá se pro nastavení zarážek dat, které jsou založeny na řetězci, který může uživatel zadat z integrovaného vývojového prostředí (IDE).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Členové
`pThread`\
[Objekt IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) který představuje vlákno, na kterém dojde k zarážky.

`bstrContext`\
Kontext zarážky v rámci kódu, obvykle název metody nebo funkce, jak je vidět na zásobníku volání.

`bstrDataExpr`\
Datový řetězec, který uživatel zadá, chcete-li nastavit zarážku.

`dwNumElements`\
Počet prvků v datovém řetězci, ve kterém dochází k zarážky.

## <a name="remarks"></a>Poznámky
Tato struktura je členem [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktury jako součást unie.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
