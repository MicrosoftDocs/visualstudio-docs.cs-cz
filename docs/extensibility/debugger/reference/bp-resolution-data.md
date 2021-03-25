---
description: Popisuje výsledek vazby datové zarážky.
title: BP_RESOLUTION_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 848a2b22ece8d3a51d7eef28b1f8baa7164ca22d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054709"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
Popisuje výsledek vazby datové zarážky.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_RESOLUTION_DATA {
    BSTR              bstrDataExpr;
    BSTR              bstrFunc;
    BSTR              bstrImage;
    BP_RES_DATA_FLAGS dwFlags;
} BP_RESOLUTION_DATA;
```

```csharp
public struct BP_RESOLUTION_DATA {
    public string bstrDataExpr;
    public string bstrFunc;
    public string bstrImage;
    public uint   dwFlags;
};
```

## <a name="members"></a>Členové
`bstrDataExpr`\
Datový výraz, který je svázán.

`bstrFunc`\
Název funkce, ve které je datová zarážka svázána (pokud existuje).

`bstrImage`\
Název modulu (například MyModule.dll), ve kterém je datová zarážka svázána.

`dwFlags`\
Hodnota z výčtu [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) , která popisuje způsob implementace datové zarážky.

## <a name="remarks"></a>Poznámky
Tato struktura je členem [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) struktury, která je zase členem struktury [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) vrácenou metodou [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
