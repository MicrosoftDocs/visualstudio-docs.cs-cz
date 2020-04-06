---
title: Kontrola exekuce | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2d338c5470611a5eea0c6279404c4eaddebb2d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739072"
---
# <a name="control-of-execution"></a>Řízení provádění
Ladicí modul (DE) obvykle odesílá jednu z následujících událostí jako poslední událost při spuštění:

- Událost vstupního bodu, pokud se připojuje k nově spuštěnému programu

- Událost dokončení načítání, pokud se připojujete k programu, který je již spuštěn

  Obě tyto události jsou zastavení události, což znamená, že DE čeká na odpověď od uživatele pomocí ide. Další informace naleznete v [tématu Provozní režimy](../../extensibility/debugger/operational-modes.md).

## <a name="stopping-event"></a>Zastavení události
 Při zastavení událost je odeslána do relace ladění:

1. Program a podproces, které obsahují aktuální ukazatel instrukce lze získat z rozhraní události.

2. Rozhraní IDE určuje aktuální soubor zdrojového kódu a pozici, která se zobrazí jako zvýrazněné v editoru.

3. Relace ladění obvykle reaguje na tuto první událost zastavení voláním metody **Continue** programu.

4. Program se pak spustí, dokud nenarazí na podmínku zastavení, například s chytnout zarážku. V takovém případě DE odešle událost zarážky do relace ladění. Událost zarážky je událost zastavení a DE opět čeká na odpověď uživatele.

5. Pokud se uživatel rozhodne vstoupit do, přes nebo z funkce, ide vyzve relaci ladění k `Step` volání metody programu. IDE pak předá jednotku kroku (instrukce, příkaz nebo řádek) a typ kroku (zda krok do, přes nebo z funkce). Po dokončení kroku DE odešle událost dokončení kroku do relace ladění, což je událost zastavení.

    -nebo-

    Pokud se uživatel rozhodne pokračovat v provádění z aktuálního ukazatele instrukce, ide vyzve relaci ladění k volání metody **spuštění** programu. Program pokračuje v provádění, dokud nenarazí na další podmínku zastavení.

    -nebo-

    Pokud je relace ladění ignorovat konkrétní událost zastavení, relace ladění volá metodu **Continue** programu. Pokud program byl krokování do, přes nebo z funkce, když došlo k zastavení podmínku, pak pokračuje krok.

   Programově, když DE narazí na podmínku zastavení, odešle takové události zastavení jako [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) nebo [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do správce ladění relace (SDM) pomocí rozhraní [IDebugCallBackback2.](../../extensibility/debugger/reference/idebugeventcallback2.md) De předá [Rozhraní IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) a [IDebugThread2,](../../extensibility/debugger/reference/idebugthread2.md) které představují program a vlákno obsahující aktuální ukazatel instrukce. SDM volá [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) získat horní rámec zásobníku a volání [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) získat kontext dokumentu spojené s aktuální ukazatel instrukce. Tento kontext dokumentu je obvykle název souboru zdrojového kódu, řádek a číslo sloupce. IDE používá k zvýraznění zdrojového kódu, který obsahuje aktuální ukazatel instrukce.

   SDM obvykle reaguje na tuto první událost zastavení voláním [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Program se pak spustí, dokud nenarazí na podmínku zastavení, jako je například stisknutí zarážky, v takovém případě DE odešle [rozhraní IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) do sdm. Událost zarážky je událost zastavení a DE opět čeká na odpověď uživatele.

   Pokud se uživatel rozhodne vstoupit do, přes nebo z funkce, ide vyzve SDM volat [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md). IDE pak předá [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instrukce, příkaz nebo řádek) a [STEPKIND](../../extensibility/debugger/reference/stepkind.md), to znamená, zda krok do, přes nebo z funkce. Po dokončení kroku DE odešle rozhraní [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) do SDM, což je událost zastavení.

   Pokud se uživatel rozhodne pokračovat v provádění z aktuálního ukazatele instrukce, ide požádá SDM volat [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Program pokračuje v provádění, dokud nenarazí na další podmínku zastavení.

   Pokud je ladicí balíček ignorovat konkrétní událost zastavení, ladicí balíček volá SDM, který volá [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Pokud program byl krokování do, přes nebo z funkce, když došlo k zastavení podmínku, pokračuje krok. To znamená, že program udržuje krokový stav, takže ví, jak pokračovat.

   Volání SDM provede `Step`, **Execute**a **Continue** jsou asynchronní, což znamená, že SDM očekává, že volání rychle vrátit. Pokud DE odešle Událost zastavení SDM ve `Step`stejném vlákně před , **Execute**, nebo **Pokračovat** vrátí, sDM zablokuje.

## <a name="see-also"></a>Viz také
- [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md)
