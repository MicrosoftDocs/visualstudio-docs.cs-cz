---
title: Podporované typy | Microsoft Docs
description: Seznamte se s typy událostí, Visual Studio ladění podporuje, včetně asynchronních událostí, synchronních událostí a zastavení událostí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fff86a142f541c1b17012b6190dd68e8d5628a3c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902901"
---
# <a name="supported-event-types"></a>Podporované typy událostí
Visual Studio ladění aktuálně podporuje následující typy událostí:

- Asynchronní události

   Upozorníte správce ladění relace (SDM) a integrované vývojové prostředí (IDE), že se mění stav laděné aplikace. Tyto události se zpracovávají v prostředí SDM a integrovaném vývojovém prostředí (IDE). Po zpracování události se do ladicího modulu (DE) neodesíná žádná odpověď. Rozhraní [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) a [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) jsou příklady asynchronních událostí.

- Synchronní události

   Upozorní SDM a integrované vývojové prostředí (IDE) na změnu stavu laděné aplikace. Jediným rozdílem mezi těmito událostmi a asynchronními událostmi je, že odpověď se odesílá pomocí metody [ContinueFromSynchronousEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

   Odeslání synchronní události je užitečné, pokud potřebujete, aby dešimování pokračovalo ve zpracování poté, co integrované vývojové prostředí událost přijme a zpracuje.

- Synchronní zastavení událostí nebo zastavení událostí

   Upozorní SDM a integrované vývojové prostředí (IDE) na to, že laditá aplikace zastavila provádění kódu. Při odesílání události zastavení pomocí události metody [je](../../extensibility/debugger/reference/idebugeventcallback2-event.md)vyžadován parametr [IDebugThread2.](../../extensibility/debugger/reference/idebugthread2.md) Zastavení událostí pokračuje voláním jedné z následujících metod:

  - [Spuštěním](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Krok](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Pokračovat](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Rozhraní [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) a [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) jsou příklady zastavení událostí.

  > [!NOTE]
  > Asynchronní události zastavení se nepodporují. Odeslání asynchronní události zastavení je chybou.

## <a name="discussion"></a>Diskuse
 Skutečná implementace událostí závisí na návrhu destrukce. Typ každé odeslané události je určen jeho atributy, které jsou nastaveny při návrhu DE. Například jeden DE může odeslat [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) jako asynchronní událost, zatímco jiný může odeslat jako událost zastavení.

 Následující tabulka určuje, které parametry programu a vlákna jsou vyžadovány pro které události a typy událostí. Každá událost může být synchronní. Žádná událost musí být synchronní.

> [!NOTE]
> Rozhraní [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) je vyžadované pro všechny události.

|Událost|IDebugProgram2|IDebugThread2|Zastavení událostí|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Povoleno, ale nevyžaduje se|Povoleno, ale nevyžaduje se|No|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Povoleno, ale nevyžaduje se|Povoleno, ale nevyžaduje se|No|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Povoleno, ale nevyžaduje se|Povoleno, ale nevyžaduje se|No|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Povoleno, ale nevyžaduje se|Povoleno, ale nevyžaduje se|No|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Vyžadováno|Vyžadováno|No|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Nepovolené|Nepovolené|No|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Nepovolené|Nepovolené|No|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Povoleno, ale nevyžaduje se|Povoleno, ale nevyžaduje se|Může být|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Povoleno, ale nevyžaduje se|Povoleno, ale nevyžaduje se|Může být|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Povoleno, ale nevyžaduje se|Povoleno, ale nevyžaduje se|Může být|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Vyžadováno|Povoleno, ale nevyžaduje se|No|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Povoleno, ale nevyžaduje se|Povoleno, ale nevyžaduje se|No|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Vyžadováno|Povoleno, ale nevyžaduje se|No|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Vyžadováno|Povoleno, ale nevyžaduje se|No|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Vyžadováno|Povoleno, ale nevyžaduje se|No|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Vyžadováno|Povoleno, ale nevyžaduje se|No|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Povoleno, ale nevyžaduje se|Povoleno, ale nevyžaduje se|No|
|IDebugStopCompleteEvent2|Vyžadováno|Vyžadováno|Yes|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Vyžadováno|Vyžadováno|Yes|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Povoleno, ale nevyžaduje se|Povoleno, ale nevyžaduje se|No|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Vyžadováno|Vyžadováno|No|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Vyžadováno|Vyžadováno|No|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Povoleno, ale nevyžaduje se|Povoleno, ale nevyžaduje se|No|

## <a name="see-also"></a>Viz také
- [Odesílání událostí](../../extensibility/debugger/sending-events.md)
