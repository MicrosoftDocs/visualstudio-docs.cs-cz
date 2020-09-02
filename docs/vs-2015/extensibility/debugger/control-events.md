---
title: Události ovládacího prvku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4073da9036e11f90fbf7202095e70fce797ea015
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62414630"
---
# <a name="control-events"></a>Události ovládacích prvků
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
