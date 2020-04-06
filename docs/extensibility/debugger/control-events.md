---
title: Kontrolní události | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2c3ad9c9b63923bdf2f107e7bc582f3c76cd62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739083"
---
# <a name="control-events"></a>Kontrolní události
Během řízeného provádění programu je nutné odeslat události. Všechny události jsou odesílány pomocí rozhraní [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) a mají atributy, které vyžadují implementaci metody [IDebugEvent2::GetAttributes.](../../extensibility/debugger/reference/idebugevent2-getattributes.md)

## <a name="additional-methods"></a>Další metody
 Některé události vyžadují implementaci dalších metod, a to následovně:

- Odeslání rozhraní [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) při inicializování ladicího stroje (DE) vyžaduje implementaci metody [IDebugEngineCreateEvent2::GetEngine.](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)

- Ovládací prvek spuštění vyžaduje implementaci takových událostí ovládacího prvku, jako jsou rozhraní [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) a[IDebugStepCompleteEvent2.](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) **IDebugBreakEvent2** je vyžadovánpouze pro asynchronní přestávky.

- Krokování do funkcí vyžaduje implementaci rozhraní [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) a jeho metod.

  Události odvozené z zarážek vyžadují implementaci metod [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)a [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) a také metod [IDebugBreakpointBoundEvent2::GetPendingBreakpointpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) a [EnumBoundBreakpoints.](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)

  Vyhodnocení asynchronního výrazu vyžaduje implementaci rozhraní [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) a jeho metod [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[a GetResult.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)

  Synchronní události vyžadují implementaci metody [IDebugEngine2::ContinueFromSynchronousEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

  Pro váš motor psát výstup ve stylu řetězce, je nutné implementovat [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) metoda.

## <a name="see-also"></a>Viz také
- [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
