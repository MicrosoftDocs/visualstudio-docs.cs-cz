---
title: EVENTATTRIBUTES | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c479058a5e6abb61fb419425706d2a8b26858d04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737059"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Určuje atributy události.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>Fields (Pole)
`EVENT_ASYNCHRONOUS`\
Označuje, že událost je asynchronní a není potřeba žádná odpověď na událost.

`EVENT_SYNCHRONOUS`\
Označuje, že událost je synchronní; odpověď pomocí [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Označuje, že se jedná o událost zastavení. Musí být kombinována `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS`s jedním nebo .

`EVENT_ASYNC_STOP`\
Označuje událost asynchronního zastavení. V současné době žádná taková událost neexistuje. Tento příznak je pouze zástupný symbol.

`EVENT_SYNC_STOP`\
Označuje událost synchronního zastavení `EVENT_SYNCHRONOUS` (kombinace `EVENT_STOPPING`a ). Tato hodnota je použita ladicí modul (DE) při odeslání zastavení události. Odpověď je provedena prostřednictvím volání [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md), nebo [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Označuje událost, která je odeslána okamžitě a synchronně do ide. Tento příznak je kombinován s `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS`jinými `EVENT_SYNC_STOP` příznaky, jako je , nebo k označení typu události a skutečnost, že mechanismus odpovědi (pokud existuje) je znám.

`EVENT_EXPRESSION_EVALUATION`\
Událost je výsledkem vyhodnocení výrazu.

## <a name="remarks"></a>Poznámky
Tyto hodnoty jsou `dwAttrib` předány v parametru [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metody.

Tyto hodnoty mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
