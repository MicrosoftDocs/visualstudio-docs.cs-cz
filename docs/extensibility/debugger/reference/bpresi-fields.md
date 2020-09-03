---
title: BPRESI_FIELDS | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737718"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Určuje informace, které mají být načteny o úspěšném vyřešení zarážky.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Pole
`BPRESI_BPRESLOCATION`\
Inicializujte nebo použijte `bpResLocation` pole (umístění rozlišení zarážky) struktury [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) .

`BPRESI_PROGRAM`\
Inicializujte nebo použijte `pProgram` pole `BP_RESOLUTION_INFO` struktury.

`BPRESI_THREAD`\
Inicializujte nebo použijte `pThread` pole `BP_RESOLUTION_INFO` struktury.

`BPRESI_ALLFIELDS`\
Určuje všechna pole.

## <a name="remarks"></a>Poznámky
Předána metodě [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) , která označuje, která pole struktury [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) mají být inicializována.

Tyto příznaky slouží také k označení toho, která pole `BP_RESOLUTION_INFO` struktury jsou použita a platná při vrácení této struktury.

Tyto hodnoty mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
