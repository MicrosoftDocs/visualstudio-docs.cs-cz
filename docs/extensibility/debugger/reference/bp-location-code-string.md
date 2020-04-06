---
title: BP_LOCATION_CODE_STRING | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 0fc0d9a053faf69fde500333ab0faafa0e8d3448
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737982"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
Používá se pro nastavení zarážek kódu na základě řetězce, který může uživatel zadat z integrovaného vývojového prostředí (IDE).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>Členové
`bstrContext`\
Kontext zarážky v rámci kódu, obvykle název metody nebo funkce, jak je vidět na zásobníku volání.

`bstrCodeExpr`\
Řetězec, který uživatel zadá k popisu zarážky kódu.

## <a name="remarks"></a>Poznámky
Tato struktura je členem [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktury jako součást unie.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
