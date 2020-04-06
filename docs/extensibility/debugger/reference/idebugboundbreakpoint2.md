---
title: IDebugBoundBreakpoint2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4d22b10085baefeb3a0286c1b4edcb5876c0dac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735420"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Toto rozhraní představuje zarážku, která je vázána na umístění kódu.

## <a name="syntax"></a>Syntaxe

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní jako součást jeho podporu pro zarážky.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) vytvoří toto rozhraní. Volání [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) a [Další](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) můžete také získat toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugBoundBreakpoint2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Získá čekající zarážka, ze kterého byla vytvořena zadaná vázaná zarážka.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Získá stav této vázané zarážky.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Získá aktuální počet přístupů pro tuto vázanou zarážku.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Získá rozlišení zarážky, která popisuje tuto zarážku.|
|[Povolení](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Povolí nebo zakáže zarážku.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Nastaví počet přístupů pro tuto vázanou zarážku.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Nastaví nebo změní podmínku přidruženou k této vázané zarážky.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Nastaví nebo změní počet průchodů přidružených k této vázané zarážky.|
|[Odstranit](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Odstraní zarážku.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Další](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Vytvořit vazbu](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
