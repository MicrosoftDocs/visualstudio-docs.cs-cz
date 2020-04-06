---
title: Provozní režimy | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027152b2b2fc18b509a687220e5d963ea1b7e721
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738280"
---
# <a name="operational-modes"></a>Provozní režimy
Existují tři režimy, ve kterých může ide pracovat, a to následovně:

- [Režim návrhu](#vsconoperationalmodesanchor1)

- [Režim spuštění](#vsconoperationalmodesanchor2)

- [Režim přerušení](#vsconoperationalmodesanchor3)

  Jak vlastní ladicí modul (DE) přechody mezi těmito režimy je rozhodnutí implementace, která vyžaduje, abyste byli obeznámeni s mechanismy přechodu. DE může nebo nemusí přímo implementovat tyto režimy. Tyto režimy jsou opravdu ladění režimy balíčku, které přepínají na základě akce uživatele nebo události z DE. Například přechod z režimu spuštění do režimu přerušení je podněcován událostí zastavení z DE. Přechod z break do režimu spuštění nebo krok režimu je podněcován uživatelem provádění operací, jako je krok nebo spustit. Další informace o přechodech DE naleznete [v tématu Řízení provádění](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a>Režim návrhu
 Režim návrhu je nespuštěný stav ladění sady Visual Studio, během kterého můžete nastavit funkce ladění v aplikaci.

 V režimu návrhu se používá pouze několik ladicích funkcí. Vývojář se může rozhodnout nastavit zarážky nebo vytvořit výrazy sledování. De je nikdy načten nebo volána, zatímco rozhraní IDE je v režimu návrhu. Interakce s DE probíhá pouze v režimu běhu a přerušení.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a>Režim spuštění
 Ke spuštění režimu dochází při spuštění programu v relaci ladění v ide. Aplikace se spustí až do ukončení, dokud je přístupů zarážky nebo dokud není vyvolána výjimka. Když aplikace spustí ukončení, DE přechody do režimu návrhu. Při zásahu zarážky nebo je vyvolána výjimka DE přechody do režimu přerušení.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a>Režim přerušení
 Režim přerušení nastane, když je pozastaveno provádění programu ladění. Break režim nabízí vývojáři snímek aplikace v době přerušení a umožňuje vývojáři analyzovat stav aplikace a změnit způsob spuštění aplikace. Vývojář může zobrazit a upravit kód, prozkoumat nebo upravit data, restartovat aplikaci, ukončit provádění nebo pokračovat v provádění ze stejného bodu.

 Režim přerušení je zadán, když DE odešle událost synchronního zastavení. Synchronní zastavení události, také volal zastavení události, upozornit správce ladění relace (SDM) a IDE, že aplikace, která je laděna zastavil a provádění kódu. [Rozhraní IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) a [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) jsou příklady zastavení událostí.

 Zastavení události pokračují voláním jedné z následujících metod, které převádí ladicí program z režimu přerušení na režim spuštění nebo krok:

- [Spuštění](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Krok](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Pokračovat](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a>Krokový režim
 Krok režimu dochází, když program kroky k dalšímu řádku kódu, nebo do, přes nebo z funkce. Krok je proveden voláním metody [Step](../../extensibility/debugger/reference/idebugprocess3-step.md). Tato metoda `DWORD`vyžaduje s, které určují [stepunit](../../extensibility/debugger/reference/stepunit.md) a [STEPKIND](../../extensibility/debugger/reference/stepkind.md) výčty jako vstupní parametry.

 Když program úspěšně kroky k dalšímu řádku kódu nebo do funkce, nebo běží na kurzor nebo nastavit zarážku, DE automaticky přejde zpět do režimu přerušení.

## <a name="see-also"></a>Viz také
- [Řízení provádění](../../extensibility/debugger/control-of-execution.md)
