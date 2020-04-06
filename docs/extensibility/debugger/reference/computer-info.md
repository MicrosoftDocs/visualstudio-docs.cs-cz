---
title: COMPUTER_INFO | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27794dff51646b72dbbfda81ead02e5206ade78b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737665"
---
# <a name="computer_info"></a>COMPUTER_INFO
Popisuje počítač, ve kterém je ladicí program spuštěn.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagCOMPUTER_INFO
{
    WORD wProcessorArchitecture;
    WORD wSuiteMask;
    DWORD dwOperatingSystemVersion;
} COMPUTER_INFO;
```

```csharp
public struct COMPUTER_INFO
{
    public ushort wProcessorArchitecture;
    public ushort wSuiteMask;
    public uint dwOperatingSystemVersion;
}
```

## <a name="members"></a>Členové
`wProcessorArchitecture`\
Identifikuje architekturu mikroprocesoru.

`wSuiteMask`\
Identifikuje masku apartmá.

`dwOperatingSystemVersion`\
Číslo verze operačního systému.

## <a name="remarks"></a>Poznámky
Tato struktura je vrácena [metodou GetComputerInfo.](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)

## <a name="requirements"></a>Požadavky
Záhlaví: Msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
