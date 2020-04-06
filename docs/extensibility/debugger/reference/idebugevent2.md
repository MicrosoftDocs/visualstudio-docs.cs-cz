---
title: IDebugEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6341f8003b962a7f45420b076b23623ebdaf861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729909"
---
# <a name="idebugevent2"></a>IDebugEvent2
Toto rozhraní se používá ke komunikaci kritické informace o ladění, jako je například zastavení na zarážky a nedůležité informace, jako je například ladicí zpráva.

## <a name="syntax"></a>Syntaxe

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) a dodavatel vlastního portu implementují toto rozhraní na stejném objektu jako všechna ostatní rozhraní událostí.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pomocí argumentu ID rozhraní , který je dán [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) nebo [události](../../../extensibility/debugger/reference/idebugportevents2-event.md), zavolá správce ladění `IDebugEvent2` relace (SDM) rozhraní [QueryInterface](/cpp/atl/queryinterface) v rozhraní, aby získal příslušné rozhraní události.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugEvent2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Získá atributy pro tuto událost ladění.|

## <a name="remarks"></a>Poznámky
 Konkrétnější rozhraní událostí, například [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), nejsou odvozeny z rozhraní IDebugEvent2, ale jsou místo `IDebugEvent2`toho implementovány jako samostatné rozhraní na stejném objektu jako .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [Událost](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
