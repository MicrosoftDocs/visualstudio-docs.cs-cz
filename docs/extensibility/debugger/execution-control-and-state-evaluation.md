---
title: Řízení provádění a vyhodnocení stavu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738752"
---
# <a name="execution-control-and-state-evaluation"></a>Řízení provádění a vyhodnocení stavu
Ladění aplikace vyžaduje implementaci takových funkcí řízení spouštění jako krokování do funkcí, zastavení na zarážekch a pokračování v provádění. Ladění sady Visual Studio zakládá své řízení provádění na události odesílané mezi komponentami ladicího programu.

## <a name="in-this-section"></a>V této části
 [Řízení programu](../../extensibility/debugger/program-control.md) Uvádí následující rutiny, které se vyskytují na úrovni programu: nastavení dalšího příkazu, spuštění, krokování, pokračování, pozastavení a obnovení.

 [Metody související se zarážkami](../../extensibility/debugger/breakpoint-related-methods.md) Definuje vázané a nedokončené typy zarážek, které podporuje Visual Studio.

 [Vyhodnocení zásobníku volání](../../extensibility/debugger/call-stack-evaluation.md) Popisuje implementaci metod, které umožňují zobrazení rámců zásobníku volání v průběhu režimu přerušení.

 [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Vysvětluje, jakým způsobem se při analýze a vyhodnocení výrazu zadaného do jednoho z oken rozhraní IDE účastní funkce ladění (DE), vyhodnocení výrazu (EE) a správce ladění relací.

 [Události ovládacích prvků](../../extensibility/debugger/control-events.md) Popisuje rozhraní používané k posílání událostí během kontrolovaného provádění programu.
