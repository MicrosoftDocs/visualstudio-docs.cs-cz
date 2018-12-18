---
title: Podporované typy událostí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f711b3a2e131baf5f7e480982ff34dc7ef89614
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949354"
---
# <a name="supported-event-types"></a>Podporované typy událostí
Ladění aplikace Visual Studio nyní podporuje následující typy událostí:  
  
- Asynchronní události  
  
   Upozornit správce ladění relace (SDM) a integrované vývojové prostředí, která se mění stav právě laděné aplikace. Tyto události se zpracovávají ve volném čase SDM a rozhraní IDE. Žádná odpověď se odešle do ladicího stroje (DE) po zpracování události. [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) a [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) rozhraní jsou příklady asynchronní událostí.  
  
- Synchronní události  
  
   Upozornění SDM a integrované vývojové prostředí, která se mění stav právě laděné aplikace. Jediným rozdílem mezi těmito události a asynchronní události je odeslání odpovědi prostřednictvím [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) metody.  
  
   Odesílání synchronní událostí je užitečné, pokud je třeba vaše DE pokračovat zpracování po integrovaného vývojového prostředí přijímá a zpracovává události.  
  
- Synchronní události zastavení nebo zastavení událostí  
  
   Upozornění SDM a rozhraní IDE, že právě laděné aplikace ukončila provádění kódu. Při odesílání událostí ukončení pomocí metody [události](../../extensibility/debugger/reference/idebugeventcallback2-event.md), [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) parametr je povinný. Ukončení události pocházejí voláním jedné z následujících metod:  
  
  - [Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
  - [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
    Rozhraní [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) a [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) patří události zastavení.  
  
  > [!NOTE]
  >  Asynchronní zastavení událostí nejsou podporovány. Jedná se o chybu pro odeslání události asynchronní zastavení.  
  
## <a name="discussion"></a>Diskuse  
 Skutečná implementace události závisí na návrhu vaší DE. Typ každá událost odeslaná je určen podle jeho atributy, které jsou nastaveny při návrhu DE. Například může odeslat jeden DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) jako asynchronní událost, zatímco jiné mohou odeslat jako událostí ukončení.  
  
 Následující tabulka určuje, které aplikace a vlákna parametry jsou povinné, pro které události, stejně jako typy událostí. Jakákoli událost může být synchronní. Žádné události musí být synchronní.  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) rozhraní se ale vyžaduje pro všechny události.  
  
|Událost|IDebugProgram2|IDebugThread2|Zastavuje se události|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Může, ale nevyžadováno|Může, ale nevyžadováno|Ne|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Požadováno|Požadováno|Ano|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Může, ale nevyžadováno|Může, ale nevyžadováno|Ne|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Může, ale nevyžadováno|Může, ale nevyžadováno|Ne|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Může, ale nevyžadováno|Může, ale nevyžadováno|Ne|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Požadováno|Požadováno|Ano|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Požadováno|Požadováno|Ne|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Nepovoleno|Nepovoleno|Ne|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Nepovoleno|Nepovoleno|Ne|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Požadováno|Požadováno|Ano|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Může, ale nevyžadováno|Může, ale nevyžadováno|Může být|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Požadováno|Požadováno|Ano|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Může, ale nevyžadováno|Může, ale nevyžadováno|Může být|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Požadováno|Požadováno|Ano|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Požadováno|Požadováno|Ano|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Může, ale nevyžadováno|Může, ale nevyžadováno|Může být|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Požadováno|Může, ale nevyžadováno|Ne|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Může, ale nevyžadováno|Může, ale nevyžadováno|Ne|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Požadováno|Může, ale nevyžadováno|Ne|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Požadováno|Může, ale nevyžadováno|Ne|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Požadováno|Může, ale nevyžadováno|Ne|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Požadováno|Může, ale nevyžadováno|Ne|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Může, ale nevyžadováno|Může, ale nevyžadováno|Ne|  
|IDebugStopCompleteEvent2|Požadováno|Požadováno|Ano|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Požadováno|Požadováno|Ano|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Může, ale nevyžadováno|Může, ale nevyžadováno|Ne|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Požadováno|Požadováno|Ne|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Požadováno|Požadováno|Ne|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Může, ale nevyžadováno|Může, ale nevyžadováno|Ne|  
  
## <a name="see-also"></a>Viz také:  
 [Odesílání událostí](../../extensibility/debugger/sending-events.md)