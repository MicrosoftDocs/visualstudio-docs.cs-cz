---
title: BP_LOCATION_CODE_ADDRESS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: c215630e522adabdbd285e00d4bcd87cae22a931
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738038"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
Popisuje umístění zarážky na adrese v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>Členové
`bstrContext`\
Kontext zarážky, obvykle název metody nebo funkce, jak je vidět na zásobníku volání.

`bstrModuleUrl`\
Adresa URL modulu, který obsahuje zarážku.

`bstrFunction`\
Název funkce, která obsahuje zarážku.

`bstrAddress`\
Adresa zarážky, která je analyzována vyhodnocenívýrazu svázat s [Objekt IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

## <a name="remarks"></a>Poznámky
Tato struktura je členem [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktury jako součást unie.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
