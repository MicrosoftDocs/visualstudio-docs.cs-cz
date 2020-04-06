---
title: BP_ERROR_TYPE | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e777e1f8cb67187a81f8f3bb4f79299939bfa31c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738077"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
Určuje typ chyby zarážky.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>Fields (Pole)
`BPET_NONE`\
Neurčuje žádnou chybu zarážky.

`BPET_TYPE_WARNING`\
Určuje chybu zarážky ve stylu varovného stylu.

`BPET_TYPE_ERROR`\
Určuje chybu zarážky chybového stylu.

`BPET_SEV_HIGH`\
Určuje chybu zarážky s vysokou závažností.

`BPET_SEV_GENERAL`\
Určuje chybu zarážky se střední závažností.

`BPET_SEV_LOW`\
Určuje chybu zarážky s nízkou závažností.

`BPET_TYPE_MASK`\
Určuje chybu zarážky ve stylu masky.

`BPET_SEV_MASK`\
Určuje chybu zarážky ve stylu masky závažnosti.

`BPET_GENERAL_WARNING`\
Určuje chybu zarážky ve stylu obecného upozornění.

`BPET_GENERAL_ERROR`\
Určuje chybu zarážky ve stylu obecné chyby.

`BPET_ALL`\
Určuje všechny typy chyb zarážky.

## <a name="remarks"></a>Poznámky
Tyto hodnoty mohou být kombinovány `OR` s bitovým a použít pro `dwType` člen [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury. Předánjako parametr metodě [EnumErrorBreakpoints.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)

Typ chyby zarážky se skládá z typu a závažnosti. To znamená, že typ chyby zarážky není `BPET_TYPE_ERROR`nikdy jen typ (například `BPET_SEV_GENERAL`,) nebo závažnost (například ) sama o sobě. `BPET_GENERAL_WARNING`a `BPET_GENERAL_ERROR` poskytují předdefinované hodnoty pro obecné upozornění a chybové zarážky.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
