---
title: Provozní režimy | Microsoft Docs
description: Přečtěte si o třech režimech, ve kterých může IDE fungovat, což jsou režim návrhu, režim běhu a režim přerušení.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: cabf32dcbe8b4d2e925bcfd48635063ecd0a5b74
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606603"
---
# <a name="operational-modes"></a>Provozní režimy
Existují tři režimy, ve kterých může IDE pracovat, následovně:

- [Režim návrhu](#vsconoperationalmodesanchor1)

- [Režim spuštění](#vsconoperationalmodesanchor2)

- [Režim přerušení](#vsconoperationalmodesanchor3)

  Způsob, jakým vaše vlastní moduly ladění (DE) mění mezi těmito režimy, je rozhodnutí o implementaci, které vyžaduje, abyste se seznámili s mechanismy přechodu. DE květen nebo nemusí přímo implementovat tyto režimy. Tyto režimy jsou opravdu ladit režimy balíčku, které se přepínají na základě akce uživatele nebo událostí z DE. Například přechod z režimu spuštění do režimu přerušení je podněcována událostí zastavení z DE. Přechod z přerušení na režim spuštění nebo krok je nápomocen uživatel, který provádí operace, jako je krok nebo provedení. Další informace o zrušení přechodů naleznete v tématu [řízení provádění](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Režim návrhu
 Režim návrhu je nespuštěný stav ladění sady Visual Studio, během kterého lze v aplikaci nastavit funkce ladění.

 V režimu návrhu se používá jenom několik funkcí ladění. Vývojář se může rozhodnout pro nastavování zarážek nebo vytváření výrazů kukátka. DE není nikdy načtena nebo volána, když je IDE v režimu návrhu. Interakce s nástrojem DE probíhá pouze v režimu spuštění a přerušení.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Režim spuštění
 Režim spuštění nastane, když se program spustí v ladicí relaci v integrovaném vývojovém prostředí. Aplikace se spustí do ukončení, dokud není dosaženo zarážky nebo dokud není vyvolána výjimka. Když aplikace běží na ukončení, DE přejde do režimu návrhu. Když je dosaženo zarážky nebo je vyvolána výjimka, příkaz DE přejde do režimu přerušení.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Režim přerušení
 Režim přerušení nastane, pokud je spuštění ladicího programu pozastaveno. Režim přerušení nabízí vývojářům snímek aplikace v době přerušení a umožňuje vývojářům analyzovat stav aplikace a změnit způsob, jakým se aplikace spustí. Vývojář může zobrazit a upravit kód, kontrolovat nebo upravovat data, restartovat aplikaci, ukončit provádění nebo pokračovat v provádění ze stejného bodu.

 Režim přerušení je zadán, když DE odešle synchronní událost zastavení. Synchronní zastavení událostí, označovaných také jako zastavování událostí, upozorní správce ladění relace (SDM) a rozhraní IDE, které aplikace Laděna, zastavila provádění kódu. Rozhraní [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) a [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) jsou příklady událostí zastavení.

 Zastavení událostí pokračuje voláním jedné z následujících metod, které převedou ladicí program z režimu přerušení na spuštění nebo krokový režim:

- [Spuštěním](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Krok](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Pokračovat](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Režim kroku
 Krokový režim nastane, pokud program provede kroky na další řádek kódu, nebo do, nad nebo mimo funkci. Krok je proveden voláním [kroku](../../extensibility/debugger/reference/idebugprocess3-step.md)metody. Tato metoda vyžaduje `DWORD` s, aby jako vstupní parametry určovala výčty [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) a [STEPKIND](../../extensibility/debugger/reference/stepkind.md) .

 Když se program úspěšně doplní na další řádek kódu nebo do funkce nebo se spustí na kurzor nebo na nastavenou zarážku, příkaz DE automaticky přejde zpět do režimu přerušení.

## <a name="see-also"></a>Viz také
- [Řízení provádění](../../extensibility/debugger/control-of-execution.md)
