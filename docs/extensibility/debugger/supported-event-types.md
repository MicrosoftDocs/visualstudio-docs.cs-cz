---
title: Podporované typy událostí | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94e26897c50fd7e10a8b831655610848cb93043f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712804"
---
# <a name="supported-event-types"></a>Podporované typy událostí
Ladění sady Visual Studio aktuálně podporuje následující typy událostí:

- Asynchronní události

   Upozorněte správce ladění relace (SDM) a ide, že se mění stav laděné aplikace. Tyto události jsou zpracovávány ve volném čase SDM a IDE. Po zpracování události není odeslána žádná odpověď ladicímu modulu (DE). Rozhraní [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) a [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) jsou příklady asynchronních událostí.

- Synchronní události

   Upozornit SDM a IDE, že stav aplikace, která je laděna se mění. Jediný rozdíl mezi těmito událostmi a asynchronní události je, že odpověď je odeslána pomocí [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) metody.

   Odeslání synchronní události je užitečné, pokud potřebujete, aby de pokračovat ve zpracování po ide obdrží a zpracuje událost.

- Synchronní zastavení událostí nebo zastavení událostí

   Upozorněte SDM a IDE, že aplikace, která je laděna, zastavila provádění kódu. Při odeslání události zastavení pomocí metody [Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)je vyžadován parametr [IDebugThread2.](../../extensibility/debugger/reference/idebugthread2.md) Zastavení události pokračují volání mj.

  - [Spuštění](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Krok](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Pokračovat](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Rozhraní [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) a [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) jsou příklady zastavení událostí.

  > [!NOTE]
  > Asynchronní zastavení události nejsou podporovány. Je chyba odeslat asynchronní zastavení události.

## <a name="discussion"></a>Diskuse
 Skutečná implementace událostí závisí na návrhu vašeho DE. Typ každé odeslané události je určen jeho atributy, které jsou nastaveny při návrhu DE. Například jeden DE může odeslat [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) jako asynchronní událost, zatímco jiný může odeslat jako zastavení události.

 Následující tabulka určuje, které parametry programu a podprocesu jsou požadovány pro které události a také typy událostí. Každá událost může být synchronní. Žádná událost nemusí být synchronní.

> [!NOTE]
> [Rozhraní IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) je vyžadováno pro všechny události.

|Událost|IDebugProgram2|IDebugThread2|Zastavení událostí|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Požaduje se|Požaduje se|Ano|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Požaduje se|Požaduje se|Ano|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Požaduje se|Požaduje se|Ne|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Nepovolené|Nepovolené|Ne|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Nepovolené|Nepovolené|Ne|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Požaduje se|Požaduje se|Ano|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Může být|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Požaduje se|Požaduje se|Ano|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Může být|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Požaduje se|Požaduje se|Ano|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Požaduje se|Požaduje se|Ano|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Může být|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Požaduje se|Povoleno, ale není vyžadováno|Ne|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Požaduje se|Povoleno, ale není vyžadováno|Ne|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Požaduje se|Povoleno, ale není vyžadováno|Ne|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Požaduje se|Povoleno, ale není vyžadováno|Ne|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Požaduje se|Povoleno, ale není vyžadováno|Ne|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|IDebugStopCompleteEvent2|Požaduje se|Požaduje se|Ano|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Požaduje se|Požaduje se|Ano|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Požaduje se|Požaduje se|Ne|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Požaduje se|Požaduje se|Ne|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|

## <a name="see-also"></a>Viz také
- [Odesílání událostí](../../extensibility/debugger/sending-events.md)
