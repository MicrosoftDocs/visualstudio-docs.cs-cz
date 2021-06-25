---
title: Provozní režimy | Microsoft Docs
description: Seznamte se se třemi režimy, ve kterých může integrované vývojové prostředí fungovat, což jsou režim návrhu, režim spuštění a režim přerušení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 559df92545f4c14eb0575e7ef758e73028349b76
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899105"
---
# <a name="operational-modes"></a>Provozní režimy
Existují tři režimy, ve kterých může integrované vývojové prostředí fungovat:

- [Režim návrhu](#vsconoperationalmodesanchor1)

- [Režim spuštění](#vsconoperationalmodesanchor2)

- [Režim přerušení](#vsconoperationalmodesanchor3)

  Způsob, jakým vlastní ladicí modul (DE) přechází mezi těmito režimy, je rozhodnutí o implementaci, které vyžaduje, abyste znají mechanismy přechodu. De může nebo nemusí tyto režimy implementovat přímo. Tyto režimy jsou ve skutečnosti režimy ladění balíčků, které se přepíná na základě akce uživatele nebo událostí z DE. Například přechod z režimu spuštění do režimu přerušení je zmírněn zastavením události z DE. Přechod z režimu break do režimu spuštění nebo krokového režimu je zmírněn tím, že uživatel provádí operace, jako je krok nebo spuštění. Další informace o přechodech DE najdete v tématu [Řízení provádění](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Režim návrhu
 Režim návrhu je nerušovací stav ladění Visual Studio, během kterého můžete v aplikaci nastavit funkce ladění.

 Během režimu návrhu se používá pouze několik funkcí ladění. Vývojář se může rozhodnout nastavit zarážky nebo vytvořit výrazy hodinek. De se nikdy nenačítá ani nevolal, když je integrované vývojové prostředí (IDE) v režimu návrhu. Interakce s DE probíhá pouze v režimu spuštění a přerušení.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Režim spuštění
 Režim spuštění nastane, když program běží v ladicí relaci v integrovaném vývojovém prostředí (IDE). Aplikace běží až do ukončení, dokud se nedosáhne zarážky, nebo dokud není vyvolána výjimka. Když se aplikace spustí k ukončení, destrukce přechází do režimu návrhu. Když dojde k zarážce nebo dojde k výjimce, destrukce přechází do režimu přerušení.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Režim přerušení
 Režim přerušení nastane, když je spuštění ladicího programu pozastavené. Režim přerušení nabízí vývojáři snímek aplikace v době přerušení a umožňuje vývojáři analyzovat stav aplikace a změnit způsob spuštění aplikace. Vývojář může zobrazit a upravovat kód, zkoumat nebo upravovat data, restartovat aplikaci, ukončit provádění nebo pokračovat v provádění od stejného bodu.

 Režim přerušení se zadá, když DE odešle synchronní událost zastavení. Synchronní události zastavení, také nazývané události zastavení, upozorní správce ladění relace (SDM) a integrované vývojové prostředí (IDE), že laditá aplikace zastavila provádění kódu. Rozhraní [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) a [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) jsou příklady zastavení událostí.

 Zastavení událostí pokračuje voláním jedné z následujících metod, která ladicí program přechází z režimu přerušení do režimu spuštění nebo kroku:

- [Spuštěním](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Krok](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Pokračovat](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Krokový režim
 Režim krokování nastane, když program postupuje na další řádek kódu nebo do funkce, přehodí ji nebo ji vystupuje. Krok se provádí voláním metody [Step](../../extensibility/debugger/reference/idebugprocess3-step.md). Tato metoda vyžaduje, aby jako vstupní parametry specifikoval výčty `DWORD` [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) a [STEPKIND.](../../extensibility/debugger/reference/stepkind.md)

 Když program úspěšně prochází další řádek kódu nebo do funkce, nebo se spustí na kurzor nebo na nastavenou zarážku, DE automaticky přechází zpět do režimu přerušení.

## <a name="see-also"></a>Viz také
- [Řízení provádění](../../extensibility/debugger/control-of-execution.md)
