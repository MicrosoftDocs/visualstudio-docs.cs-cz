---
title: DEBUG_REASON | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59954ea7e89390a5e35dbe0bfb0412da1aabc80f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737419"
---
# <a name="debug_reason"></a>DEBUG_REASON
Určuje, proč byl proces spuštěn pro ladění.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Fields (Pole)
`DEBUG_REASON_ERROR`\
Došlo k nespecifické chybě (tato podmínka se používá jako výchozí podmínka, pokud se žádný z ostatních důvodů nevejde).

`DEBUG_REASON_USER_LAUNCHED`\
Proces byl spuštěn na žádost uživatele.

`DEBUG_REASON_USER_ATTACHED`\
Již spuštěný proces byl připojen uživatelem.

`DEBUG_REASON_AUTO_ATTACHED`\
Proces byl automaticky připojen k při spuštění.

`DEBUG_REASON_CAUSALITY`\
Proces byl spuštěn z důvodu události ladění *Just-In-Time* (JIT).

## <a name="remarks"></a>Poznámky
Vráceno z [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) metoda.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
