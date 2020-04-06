---
title: IDebugBreakpointErrorEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09cb93f0f16420e56104f371d9caab262873390f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735052"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Toto rozhraní informuje správce ladění relace (SDM), že čekající zarážka nemůže být vázána na načtený program, a to buď z důvodu upozornění nebo chyby.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní jako součást jeho podporu pro zarážky. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto `IDebugEvent2` rozhraní (SDM používá [QueryInterface](/cpp/atl/queryinterface) pro přístup k rozhraní).

## <a name="notes-for-callers"></a>Poznámky pro volající
 De vytvoří a odešle tento objekt události, když čekající zarážka nemůže být vázána na program, který je laděn. Událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2](../../../extensibility/debugger/reference/idebugeventcallback2.md) zajišťované sdm, když je připojena k programu, který je odladěn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugBreakpointErrorEvent2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Získá rozhraní [IDebugErrorBreakpoint2,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) který popisuje upozornění nebo chybu.|

## <a name="remarks"></a>Poznámky
 Vždy, když je zarážka vázána, událost je odeslána do SDM. Pokud zarážka nemůže `IDebugBreakpointErrorEvent2` být vázána, je odeslána; v opačném případě je [odeslána iDebugBreakpointBoundEvent2.](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)

 Například pokud se nepodaří analyzovat nebo vyhodnotit podmínku přidruženou k čekající zarážky, je odesláno upozornění, že čekající zarážka nemůže být v tuto chvíli vázána. Tato situace může nastat, pokud kód pro zarážku ještě nebyl načten.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
