---
title: Kontrola provádění a hodnocení stavu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc76ae97e8baa6ce78dd4d565109d6a19e2051e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738752"
---
# <a name="execution-control-and-state-evaluation"></a>Řízení provádění a vyhodnocení stavu
Ladění aplikace vyžaduje implementaci těchto funkcí řízení provádění, jako je krokování do funkcí, zastavení na zarážky a pokračující provádění. Visual Studio ladění zakládá jeho řízení provádění na události odeslané mezi součástmi ladicího programu.

## <a name="in-this-section"></a>V tomto oddílu
 [Řízení programu](../../extensibility/debugger/program-control.md) Uvádí následující rutiny, ke kterým dochází na úrovni programu: nastavení dalšího příkazu, provedení, krokování, pokračování, pozastavení a obnovení.

 [Metody související s zarážkem](../../extensibility/debugger/breakpoint-related-methods.md) Definuje vázané a čekající typy zarážek, které podporuje Visual Studio.

 [Vyhodnocení zásobníku volání](../../extensibility/debugger/call-stack-evaluation.md) Popisuje implementaci metod, které umožňují zobrazení rámců zásobníku zásobníku volání během režimu přerušení.

 [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Vysvětluje, jak ladicí modul (DE), vyhodnocení výrazu (EE) a správce ladění relace jsou zapojeny do analýzy a vyhodnocení výrazu zadaného do jednoho z oken ide.

 [Kontrolní události](../../extensibility/debugger/control-events.md) Popisuje rozhraní používané k odesílání událostí během řízeného provádění programu.
