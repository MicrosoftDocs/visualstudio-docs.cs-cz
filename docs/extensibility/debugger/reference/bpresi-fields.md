---
title: BPRESI_FIELDS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 837bb7d25ab8dea2b146a98cc65d320b58162685
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737718"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Určuje informace, které mají být načteny o úspěšném vyřešení zarážky.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>Fields (Pole)
`BPRESI_BPRESLOCATION`\
Inicializovat/použít `bpResLocation` pole (umístění rozlišení zarážky) struktury [BP_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-resolution-info.md)

`BPRESI_PROGRAM`\
Inicializovat/použít `pProgram` pole `BP_RESOLUTION_INFO` struktury.

`BPRESI_THREAD`\
Inicializovat/použít `pThread` pole `BP_RESOLUTION_INFO` struktury.

`BPRESI_ALLFIELDS`\
Určuje všechna pole.

## <a name="remarks"></a>Poznámky
Předána [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) metoda k označení, která pole [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struktury mají být inicializovány.

Tyto příznaky se také používají k `BP_RESOLUTION_INFO` označení, která pole struktury se používají a jsou platné při vrácení této struktury.

Tyto hodnoty mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
