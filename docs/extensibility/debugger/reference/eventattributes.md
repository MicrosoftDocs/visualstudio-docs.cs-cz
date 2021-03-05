---
description: Určuje atributy události.
title: EVENTATTRIBUTES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e6b56e815d8145e3f870468751a0978475245c86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150884"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Určuje atributy události.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Pole
`EVENT_ASYNCHRONOUS`\
Indikuje, že událost je asynchronní a není nutná žádná odpověď na událost.

`EVENT_SYNCHRONOUS`\
Indikuje, že událost je synchronní; odpovědět prostřednictvím [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Označuje, že se jedná o událost zastavení. Musí být kombinována s buď `EVENT_ASYNCHRONOUS` nebo `EVENT_SYNCHRONOUS` .

`EVENT_ASYNC_STOP`\
Označuje asynchronní zastavení události. Žádná taková událost není momentálně k dispozici. Tento příznak je pouze zástupný symbol.

`EVENT_SYNC_STOP`\
Označuje událost synchronního zastavení (kombinace `EVENT_SYNCHRONOUS` a `EVENT_STOPPING` ). Tuto hodnotu používá ladicí stroj (DE) při odesílání události zastavení. Odpověď se provádí prostřednictvím volání metody [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)nebo [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Označuje událost, která je odeslána okamžitě a synchronně na integrované vývojové prostředí (IDE). Tento příznak je kombinován s dalšími příznaky jako `EVENT_ASYNCHRONOUS` , `EVENT_SYNCHRONOUS` nebo `EVENT_SYNC_STOP` k označení typu události a faktu, že je znám mechanismus odpovědi (pokud existuje).

`EVENT_EXPRESSION_EVALUATION`\
Událost je výsledkem vyhodnocení výrazu.

## <a name="remarks"></a>Poznámky
Tyto hodnoty jsou předány v `dwAttrib` parametru metody [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .

Tyto hodnoty mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
