---
title: Podporované typy událostí | Microsoft Docs
description: Seznamte se s typy událostí, které podporuje ladění sady Visual Studio, včetně asynchronních událostí, synchronních událostí a zastavování událostí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 883c9fd51cc4dfc4f2cc2f996d24c0722478505f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079407"
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

  - [Spuštěním](../../extensibility/debugger/reference/idebugprogram2-execute.md)

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
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|No|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|No|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|No|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|No|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Vyžadováno|Vyžadováno|No|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Nepovolené|Nepovolené|No|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Nepovolené|Nepovolené|No|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Může být|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Může být|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|Může být|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Vyžadováno|Povoleno, ale není vyžadováno|No|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|No|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Vyžadováno|Povoleno, ale není vyžadováno|No|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Vyžadováno|Povoleno, ale není vyžadováno|No|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Vyžadováno|Povoleno, ale není vyžadováno|No|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Vyžadováno|Povoleno, ale není vyžadováno|No|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|No|
|IDebugStopCompleteEvent2|Vyžadováno|Vyžadováno|Yes|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|No|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Vyžadováno|Vyžadováno|No|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Vyžadováno|Vyžadováno|No|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Povoleno, ale není vyžadováno|Povoleno, ale není vyžadováno|No|

## <a name="see-also"></a>Viz také
- [Odesílání událostí](../../extensibility/debugger/sending-events.md)
