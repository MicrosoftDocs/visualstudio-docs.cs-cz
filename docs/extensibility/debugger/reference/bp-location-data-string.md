---
description: Slouží k nastavení zarážek s daty, které jsou založeny na řetězci, který uživatel může zadat z integrovaného vývojového prostředí (IDE).
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 1e4a250843ebbb6ab7680040e3aa296699e184ee
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144348"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Slouží k nastavení zarážek s daty, které jsou založeny na řetězci, který uživatel může zadat z integrovaného vývojového prostředí (IDE).

## <a name="syntax"></a>Syntax

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
Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , který představuje vlákno, na kterém se nachází zarážka.

`bstrContext`\
Kontext zarážky v rámci kódu, obvykle název metody nebo funkce, jak je vidět v zásobníku volání.

`bstrDataExpr`\
Datový řetězec, který uživatel zadá pro nastavení zarážky.

`dwNumElements`\
Počet prvků v datovém řetězci, v němž dojde k zarážce.

## <a name="remarks"></a>Poznámky
Tato struktura je členem [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktury jako součást sjednocení.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
