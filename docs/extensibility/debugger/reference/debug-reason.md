---
description: Určuje, proč byl proces spuštěn pro ladění.
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9404e4b5cfdd1f1690b0fe76d0cd5e98cc90d2a4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170546"
---
# <a name="debug_reason"></a>DEBUG_REASON
Určuje, proč byl proces spuštěn pro ladění.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Pole
`DEBUG_REASON_ERROR`\
Objevila se nespecifická chyba (ta se používá jako výchozí podmínka, když žádný z ostatních důvodů nevyhovuje).

`DEBUG_REASON_USER_LAUNCHED`\
Proces se spustil na žádost uživatele.

`DEBUG_REASON_USER_ATTACHED`\
Již běžící proces byl připojen k uživateli.

`DEBUG_REASON_AUTO_ATTACHED`\
Proces byl automaticky připojen k době, kdy byl spuštěn.

`DEBUG_REASON_CAUSALITY`\
Proces byl spuštěn z důvodu události ladění JIT (Just *-in-time* ).

## <a name="remarks"></a>Poznámky
Vráceno z metody [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
