---
description: Určuje důvod pro modul ladění (DE), který se má připojit k uzlu programu.
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9da162dd2c477d5b901be6c622e2456f44d26a35
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085426"
---
# <a name="attach_reason"></a>ATTACH_REASON
Určuje důvod pro modul ladění (DE), který se má připojit k uzlu programu.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Pole
`ATTACH_REASON_AUTO`\
Připojte se, protože proces je aktuálně v režimu ladění.

`ATTACH_REASON_LAUNCH`\
Připojte se, protože proces byl spuštěn.

`ATTACH_REASON_USER`\
Připojte se kvůli žádosti uživatele.

## <a name="remarks"></a>Poznámky
Tyto hodnoty se používají jako parametr pro metody [připojení](../../../extensibility/debugger/reference/idebugengine2-attach.md) a [připojení](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Připojit](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
