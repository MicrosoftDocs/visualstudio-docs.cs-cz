---
title: BPERESI_FIELDS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af2f20e7d3abd79261dc18753a7eb940666fc186
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737763"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Určuje informace, které mají být načteny o neúspěšném vyřešení zarážky.

## <a name="syntax"></a>Syntaxe

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

## <a name="fields"></a>Fields (Pole)
`PERESI_BPRESLOCATION`\
Inicializovat/použít `bpResLocation` pole (umístění rozlišení zarážky) [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury.

`BPERESI_PROGRAM`\
Inicializovat/použít `pProgram` pole `BP_ERROR_RESOLUTION_INFO` struktury.

`BPERESI_THREAD`\
Inicializovat/použít `pThread` pole `BP_ERROR_RESOLUTION_INFO` struktury.

`BPERESI_MESSAGE`\
Inicializovat/použít `bstrMessage` pole `BP_ERROR_RESOLUTION_INFO` struktury.

`BPERESI_TYPE`\
Inicializovat/použít `dwType` pole (typ zarážky) `BP_ERROR_RESOLUTION_INFO` struktury.

`BPERESI_ALLFIELDS`\
Inicializovat/použít všechna `BP_ERROR_RESOLUTION_INFO` pole struktury.

## <a name="remarks"></a>Poznámky
Předánjako parametr [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metoda k označení, která pole [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury mají být inicializovány.

Tyto hodnoty se také používají k `BP_ERROR_RESOLUTION_INFO` označení, která pole ve struktuře se používají a jsou platná při vrácení této struktury.

Tyto hodnoty mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
