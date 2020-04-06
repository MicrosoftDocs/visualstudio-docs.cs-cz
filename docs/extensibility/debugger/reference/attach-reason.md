---
title: ATTACH_REASON | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca871d9dac2b6f37018af925eece5c1a6f3d1585
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738121"
---
# <a name="attach_reason"></a>ATTACH_REASON
Určuje důvod připojení ladicího modulu (DE) k uzlu programu.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
typedef DWORD ATTACH_REASON;
```

```csharp
public enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
```

## <a name="fields"></a>Fields (Pole)
`ATTACH_REASON_AUTO`\
Připojit, protože proces je aktuálně v režimu ladění.

`ATTACH_REASON_LAUNCH`\
Připojit, protože proces byl spuštěn.

`ATTACH_REASON_USER`\
Připojit z důvodu požadavku uživatele.

## <a name="remarks"></a>Poznámky
Tyto hodnoty se používají jako parametr k [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) a [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) metody.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Připojit](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
