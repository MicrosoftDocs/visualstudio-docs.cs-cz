---
description: Toto rozhraní představuje zarážku, která je vázána na umístění kódu.
title: IDebugBoundBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2726a2422c49335d9c95e7d500381ad1fdc0108
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167474"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Toto rozhraní představuje zarážku, která je vázána na umístění kódu.

## <a name="syntax"></a>Syntax

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní jako součást podpory zarážek.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní vytvoří volání [metody bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) . Toto rozhraní může získat také volání [zarážka](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) a [Další](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugBoundBreakpoint2` .

|Metoda|Popis|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Získá nevyřízenou zarážku, ze které se vytvořila zadaná vázaná zarážka.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Získá stav této vázané zarážky.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Získá aktuální počet přístupů k této vázané zarážce.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Získá rozlišení zarážky, které popisuje tuto zarážku.|
|[Povolení](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Povoluje nebo zakazuje zarážku.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Nastaví počet přístupů k této vázané zarážce.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Nastaví nebo změní podmínku přidruženou k této vázané zarážce.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Nastaví nebo změní počet průchodů přidružených k této vázané zarážce.|
|[Odstranit](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Odstraní zarážku.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Další](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Zapisovat](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
