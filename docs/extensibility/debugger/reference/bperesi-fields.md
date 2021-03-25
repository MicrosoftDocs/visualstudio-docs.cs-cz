---
description: Určuje informace, které mají být načteny o neúspěšném vyřešení zarážky.
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8164f377e56c884149fb0711286d7702fe92eb82
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067683"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Určuje informace, které mají být načteny o neúspěšném vyřešení zarážky.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Pole
`PERESI_BPRESLOCATION`\
Inicializujte nebo použijte `bpResLocation` pole (umístění rozlišení zarážky) struktury [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) .

`BPERESI_PROGRAM`\
Inicializujte nebo použijte `pProgram` pole `BP_ERROR_RESOLUTION_INFO` struktury.

`BPERESI_THREAD`\
Inicializujte nebo použijte `pThread` pole `BP_ERROR_RESOLUTION_INFO` struktury.

`BPERESI_MESSAGE`\
Inicializujte nebo použijte `bstrMessage` pole `BP_ERROR_RESOLUTION_INFO` struktury.

`BPERESI_TYPE`\
Inicializujte nebo použijte `dwType` pole (typ zarážky) `BP_ERROR_RESOLUTION_INFO` struktury.

`BPERESI_ALLFIELDS`\
Inicializujte nebo použijte všechna pole `BP_ERROR_RESOLUTION_INFO` struktury.

## <a name="remarks"></a>Poznámky
Předán jako parametr metodě [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) k určení, která pole [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury mají být inicializována.

Tyto hodnoty slouží také k označení toho, která pole ve `BP_ERROR_RESOLUTION_INFO` struktuře jsou použita a platná při vrácení této struktury.

Tyto hodnoty mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
