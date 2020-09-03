---
title: Podporované typy událostí | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712804"
---
# <a name="supported-event-types"></a>Podporované typy událostí
Ladění sady Visual Studio aktuálně podporuje následující typy událostí:

- Asynchronní události

   Upozorněte správce ladění relace (SDM) a IDE, že stav laděné aplikace se mění. Tyto události jsou zpracovávány ve volném čase modelu SDM a integrovaného vývojového prostředí (IDE). Po zpracování události není odeslána žádná odpověď do ladicího stroje (DE). Mezi Příklady asynchronních událostí patří rozhraní [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) a [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) .

- Synchronní události

   Upozorněte na SDM a IDE, že se mění stav laděné aplikace. Jediným rozdílem mezi těmito událostmi a asynchronními událostmi je, že odpověď je odeslána prostřednictvím metody [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .

   Odeslání synchronní události je užitečné, pokud potřebujete, aby bylo možné pokračovat ve zpracování poté, co IDE přijme a zpracuje událost.

- Synchronní zastavení událostí nebo zastavení událostí

   Upozorněte na SDM a IDE, že aplikace, která se právě ladí, zastavila provádění kódu. Při odeslání události zastavení prostřednictvím [události](../../extensibility/debugger/reference/idebugeventcallback2-event.md)metody je vyžadován parametr [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) . Zastavování událostí pokračuje voláním jedné z následujících metod:

  - [Spuštění](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Krok](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Pokračovat](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Rozhraní [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) a [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) jsou příklady zastavení událostí.

  > [!NOTE]
  > Asynchronní zastavení událostí se nepodporuje. Odeslání asynchronní události zastavení je chyba.

## <a name="discussion"></a>Diskuse
 Skutečná implementace událostí závisí na návrhu DE. Typ každého odeslané události je určen jeho atributy, které jsou nastaveny při návrhu DE. Například jeden DE může odeslat [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) jako asynchronní událost, zatímco další může odeslat jako událost zastavení.

 Následující tabulka určuje, které parametry programu a vlákna jsou požadovány pro které události a také pro typy událostí. Jakoukoli událost může být synchronní. Žádná událost nemusí být synchronní.

> [!NOTE]
> Pro všechny události se vyžaduje rozhraní [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) .

|Událost|IDebugProgram2|IDebugThread2|Zastavení událostí|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Vyžadováno|Vyžadováno|Ano|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Vyžadováno|Vyžadováno|Ano|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Vyžadováno|Vyžadováno|Ne|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Nepovolené|Nepovolené|Ne|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Nepovolené|Nepovolené|Ne|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Vyžadováno|Vyžadováno|Ano|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Může být|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Vyžadováno|Vyžadováno|Ano|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Může být|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Vyžadováno|Vyžadováno|Ano|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Vyžadováno|Vyžadováno|Ano|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Může být|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|IDebugStopCompleteEvent2|Vyžadováno|Vyžadováno|Ano|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Vyžadováno|Vyžadováno|Ano|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Vyžadováno|Vyžadováno|Ne|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Vyžadováno|Vyžadováno|Ne|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Ne|

## <a name="see-also"></a>Viz také
- [Odesílání událostí](../../extensibility/debugger/sending-events.md)
