---
title: Řízení spouštění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 42a95e01a44236d4f98f55f50a56cf28473ad575
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927538"
---
# <a name="control-of-execution"></a>Řízení spouštění
Ladicí stroj (DE) jednoho z následujících událostí obvykle odešle jako poslední události po spuštění:  
  
- Událost bodu položku, pokud připojení na nově otevřeném program  
  
- Událost dokončení zatížení, pokud se připojuje k programu, který je již spuštěna  
  
  Obě tyto události patří události zastavení, což znamená, že je DE čeká na odpověď od uživatele prostřednictvím integrovaného vývojového prostředí. Další informace najdete v tématu [provozní režimy](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>Zastavení událostí  
 Kdy je odesílat událostí ukončení relace ladění:  
  
1. Aplikace a vlákna, které obsahují aktuální ukazatel příkazu můžete získat rozhraní události.  
  
2. Rozhraní IDE zjistí aktuálního souboru se zdrojovým kódem a umístění, která se zobrazí jako zvýrazněné v editoru.  
  
3. Relace ladění se obvykle reakce na tento první událost zastavení voláním programu **pokračovat** metody.  
  
4. Program se pak spustí, dokud nenarazí na zastavení podmínku, třeba dosažení zarážky. V takovém případě je DE odešle událost zarážky relace ladění. Událost zarážky je zastavení, a DE znovu čeká na odpověď uživatele.  
  
5. Pokud se uživatel rozhodne krokovat do, nad nebo ve funkci, rozhraní IDE zobrazí výzvu ladicí relace pro volání programu `Step` metody. Rozhraní IDE pak předá jednotka kroku (instrukce, příkaz nebo řádek) a typ kroku (ať už krokovat do, přes nebo mimo funkci). Po dokončení kroku DE odešle událost dokončení kroku ladicí relaci, což je událostí ukončení.  
  
    -nebo-  
  
    Pokud se uživatel rozhodne má pokračovat provedením z aktuální ukazatele na instrukci, rozhraní IDE zobrazí výzvu ladicí relace pro volání programu **Execute** metody. Program pokračuje v provádění dokud nenarazí na další podmínky zastavení.  
  
    -nebo-  
  
    Pokud se bude ignorovat událostí konkrétní ukončení relace ladění, relace ladění zavolá programu **pokračovat** metody. Pokud program byl krokování do, nad nebo ve funkci, pokud došlo ke stavu zastavení, potom pokračuje v kroku.  
  
   Prostřednictvím kódu programu, když je DE narazí na podmínku přerušení, odešle tyto události zastavení jako [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) nebo [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do Správce ladění relace (SDM) prostřednictvím [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) rozhraní. Předá DE [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) a [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) rozhraní, které představují program a vlákna obsahující aktuální ukazatel příkazu. Volání SDM [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) rámec na vrcholu zásobníku a volání [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) získat kontext dokumentu spojený s aktuální instrukce ukazatel. Kontext tohoto dokumentu je obvykle zdrojový kód souboru název, řádek a sloupec číslo. Integrované vývojové prostředí, používá tato zvýrazněte zdrojový kód, který obsahuje aktuální ukazatel příkazu.  
  
   SDM obvykle reakce na tento první událost zastavení voláním [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Program pak spustí, dokud nenarazí na zastavení podmínku, třeba dosažení zarážky, odešle žádost případ DE [IDebugBreakpointEvent2 rozhraní](../../extensibility/debugger/reference/idebugbreakpointevent2.md) k SDM. Událost zarážky je zastavení, a DE znovu čeká na odpověď uživatele.  
  
   Pokud se uživatel rozhodne krokovat do, nad nebo ve funkci, rozhraní IDE zobrazí výzvu SDM volat [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md). Rozhraní IDE se pak předá [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instrukce, příkaz nebo řádek) a [STEPKIND](../../extensibility/debugger/reference/stepkind.md), to znamená, zda krokovat do, přes nebo mimo funkci. Po dokončení kroku odešle DE [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) rozhraní SDM, což je událostí ukončení.  
  
   Pokud se uživatel rozhodne má pokračovat provedením z aktuální ukazatele na instrukci, rozhraní IDE požádá SDM volat [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Program pokračuje v provádění dokud nenarazí na další podmínky zastavení.  
  
   Pokud balíček ladění bude ignorovat konkrétní zastavení událostí, zavolá ladit balíček SDM, která volá [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Pokud program byl krokování do, nad nebo ve funkci, pokud došlo ke stavu zastavení, bude pokračovat v kroku. Z toho vyplývá, že program udržuje krokování stavu, takže ví, jak pokračovat.  
  
   Volání SDM provede `Step`, **Execute**, a **pokračovat** jsou asynchronní, což znamená, SDM očekává, že volání rychle vrátit. Pokud je DE odešle SDM událostí ukončení ve stejném vlákně před `Step`, **Execute**, nebo **pokračovat** vrátí SDM přestane reagovat.  
  
## <a name="see-also"></a>Viz také:  
 [Ladění úloh](../../extensibility/debugger/debugging-tasks.md)