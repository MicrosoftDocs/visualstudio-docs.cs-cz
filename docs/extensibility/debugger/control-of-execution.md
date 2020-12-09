---
title: Řízení provádění | Microsoft Docs
description: Přečtěte si o zastavování událostí, což znamená, že příkaz DE čeká odpověď od uživatele prostřednictvím rozhraní IDE.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 88adaad3092e084841c40b5e04d45f94985a2ee8
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913877"
---
# <a name="control-of-execution"></a>Řízení provádění
Ladicí stroj (DE) obvykle odesílá jednu z následujících událostí jako poslední událost spuštění:

- Událost vstupního bodu, pokud se připojí k nově spuštěnému programu

- Událost načtení po dokončení, pokud je připojen k programu, který je již spuštěn

  Obě tyto události zastavují události, což znamená, že DE čeká odpověď od uživatele prostřednictvím rozhraní IDE. Další informace najdete v tématu [provozní režimy](../../extensibility/debugger/operational-modes.md).

## <a name="stopping-event"></a>Událost zastavení
 Při odeslání události zastavení do relace ladění:

1. Program a vlákno, které obsahují ukazatel na aktuální instrukci, lze získat z rozhraní události.

2. Rozhraní IDE Určuje aktuální soubor a polohu zdrojového kódu, který je v editoru zobrazen jako zvýrazněný.

3. Relace ladění obvykle reaguje na tuto první událost zastavení voláním metody **Continue** programu.

4. Program se pak spustí, dokud nenalezne podmínku zastavení, jako je například zarážka na zarážku. V takovém případě DE pošle událost zarážky do relace ladění. Událost zarážky je událost zastavení a příkaz DE znovu čeká na reakci uživatele.

5. Pokud se uživatel rozhodne Krokovat s vnořením funkce nebo ven, rozhraní IDE vyzve relaci ladění, aby volala `Step` metodu programu. Rozhraní IDE pak předá jednotku kroku (instrukci, příkaz nebo řádek) a typ kroku (zda se má krokovat, přenášet nebo mimo funkci). Po dokončení kroku odešle příkaz DE událost dokončení kroku do relace ladění, což je událost zastavení.

    -nebo-

    Pokud se uživatel rozhodne pokračovat v provádění z aktuálního ukazatele instrukce, IDE vyzve relaci ladění, aby volala metodu **Execute** programu. Program pokračuje v provádění, dokud nenalezne další podmínku zastavení.

    -nebo-

    Pokud relace ladění má ignorovat konkrétní událost zastavení, ladicí relace volá metodu **Continue** tohoto programu. Pokud se v programu objevila nebo převzala funkce, když se zjistil stav zastavení, pokračuje se v kroku.

   Programově, když nástroj DE narazí na stav zastavení, odešle takové události zastavení jako [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) nebo [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do Správce ladění relace (SDM) prostřednictvím rozhraní [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) . DE předá rozhraní [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) a [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , která reprezentují program, a vlákno obsahující aktuální ukazatel na instrukci. Volání SDM [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) získá horní rámec zásobníku a volá [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) pro získání kontextu dokumentu přidruženého k aktuálnímu ukazateli instrukcí. Tento kontext dokumentu je obvykle název souboru zdrojového kódu, řádku a číslo sloupce. Rozhraní IDE je používá k zvýraznění zdrojového kódu, který obsahuje ukazatel na aktuální instrukci.

   SDM obvykle reaguje na tuto první událost zastavení voláním [IDebugProgram2:: Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Program se pak spustí, dokud nenarazí na stav zastavení, jako je například zarážka na zarážce. v takovém případě příkaz DE pošle [rozhraní IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) do SDM. Událost zarážky je událost zastavení a příkaz DE znovu čeká na reakci uživatele.

   Pokud se uživatel rozhodne Krokovat s vnořením funkce a přejít na ni, IDE vyzve rozhraní SDM, aby volalo [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md). Rozhraní IDE pak předá [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instrukci, příkaz nebo řádek) a [STEPKIND](../../extensibility/debugger/reference/stepkind.md), to znamená, zda se má krokovat, přenášet nebo přenášet funkce. Po dokončení kroku příkaz DE pošle rozhraní [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) do SDM, což je událost zastavení.

   Pokud se uživatel rozhodne pokračovat v provádění z aktuálního ukazatele instrukcí, rozhraní IDE požádá o volání metody SDM, aby volala metodu [IDebugProgram2:: Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Program pokračuje v provádění, dokud nenalezne další podmínku zastavení.

   Pokud ladicí balíček má ignorovat konkrétní událost zastavení, ladicí balíček volá SDM, který volá [IDebugProgram2:: Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Pokud byl program ve fázi, kdy nebo mimo funkci, když zjistil stav zastavení, pokračuje krok. To znamená, že program udržuje stav krokování, aby věděl, jak pokračovat.

   Volání metody SDM provede, provede `Step` a **Execute** **pokračuje** , jsou asynchronní, což znamená, že model SDM očekává, že volání vrátí rychle. Pokud DE pošle událost zastavení SDM ve stejném vlákně před `Step` , **spustí** nebo **pokračuje** , model SDM přestane reagovat.

## <a name="see-also"></a>Viz také
- [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)
