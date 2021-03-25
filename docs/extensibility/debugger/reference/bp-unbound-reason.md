---
description: Poskytne důvod, proč byla zarážka nevázaná.
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13f723c6395b8b271d6f097d811c5a31569c5853
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067696"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Poskytne důvod, proč byla zarážka nevázaná.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="fields"></a>Pole
`BPUR_UNKNOWN`\
Důvod není znám.

`BPUR_CODE_UNLOADED`\
Kód, který obsahuje zarážku, byl uvolněn.

`BPUR_BREAKPOINT_REBIND`\
Zarážka byla znovu svázána s jiným umístěním. K tomu může dojít po přesunutí operace Upravit a pokračovat, nebo když je zarážka svázána se souborem s cestou, která již není platná.

`BPUR_ BREAKPOINT_ERROR`\
V případě, že je tato zarážka navázána, je určena chyba. K tomu dojde u spravovaných zarážek, jejichž podmínky již nejsou platné.

## <a name="remarks"></a>Poznámky
Vrácený metodou [getdůvod](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
