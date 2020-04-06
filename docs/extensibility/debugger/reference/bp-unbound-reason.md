---
title: BP_UNBOUND_REASON | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0ee695e1108bf9f1c6069084a0826ee23bf37d4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737782"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Poskytuje důvod, proč byla zarážka nevázaná.

## <a name="syntax"></a>Syntaxe

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

## <a name="fields"></a>Fields (Pole)
`BPUR_UNKNOWN`\
Důvod není znám.

`BPUR_CODE_UNLOADED`\
Kód, který obsahuje zarážku byl uvolněn.

`BPUR_BREAKPOINT_REBIND`\
Zarážka byla odskočit do jiného umístění. K tomu může dojít po úpravách a pokračování operací, když se přesune zarážka nebo když je zarážka vázána na soubor s cestou, která již není platná.

`BPUR_ BREAKPOINT_ERROR`\
Zarážka je určena být omylem po je vázán. K tomu dochází u spravovaných zarážek, jejichž podmínky již nejsou platné.

## <a name="remarks"></a>Poznámky
Vráceno [Metodou GetReason.](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
