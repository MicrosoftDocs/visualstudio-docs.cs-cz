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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8a48ffcb3c0409839ec9323679e396a7e23b8f3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088819"
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
