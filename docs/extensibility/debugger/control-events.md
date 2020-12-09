---
title: Události ovládacího prvku | Microsoft Docs
description: Přečtěte si o posílání událostí během kontrolovaného provádění programu pomocí rozhraní IDebugEvent2.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bf7f59384d9317e4be173c93b6165d754a35ad8f
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914241"
---
# <a name="control-events"></a>Události ovládacích prvků
Během řízeného provádění programu je nutné odesílat události. Všechny události jsou odesílány pomocí rozhraní [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) a mají atributy, které vyžadují implementaci metody [IDebugEvent2:: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) .

## <a name="additional-methods"></a>Další metody
 Některé události vyžadují implementaci dalších metod, a to následujícím způsobem:

- Odeslání rozhraní [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) při inicializaci modulu ladění (de) vyžaduje implementaci metody [IDebugEngineCreateEvent2:: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) .

- Řízení spouštění vyžaduje implementaci takových událostí ovládacích prvků jako rozhraní [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) a[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) . **IDebugBreakEvent2** se vyžaduje jenom pro asynchronní zalomení.

- Krokování do funkcí vyžaduje implementaci rozhraní [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) a jeho metod.

  Události odvozené od zarážek vyžadují implementaci rozhraní [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)a [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) a také metody [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) a [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .

  Asynchronní vyhodnocení výrazu vyžaduje, abyste implementovali rozhraní [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) a jeho metody [IDebugExpressionEvaluationCompleteEvent2:: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[a GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) .

  Synchronní události vyžadují implementaci metody [IDebugEngine2:: ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .

  Aby mohl váš stroj zapisovat výstup řetězcového stylu, je nutné implementovat metodu [IDebugOutputStringEvent2:: GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) .

## <a name="see-also"></a>Viz také
- [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
