---
title: Odeslat zprávy do okna výstup | Microsoft Docs
ms.date: 11/08/2018
ms.topic: how-to
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d3c146775ac06b3118186738ee74932a4c452a
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350469"
---
# <a name="send-messages-to-the-output-window"></a>Odesílání zpráv do okna výstupu

Můžete zapisovat zprávy za běhu do okna **výstup** pomocí <xref:System.Diagnostics.Debug> třídy nebo <xref:System.Diagnostics.Trace> třídy, která je součástí <xref:System.Diagnostics> knihovny tříd. Použijte <xref:System.Diagnostics.Debug> třídu, pokud chcete výstup pouze v *ladicí* verzi programu. Použijte <xref:System.Diagnostics.Trace> třídu, pokud chcete výstup v *ladicí* verzi i ve *verzi Release* .

## <a name="output-methods"></a>Metody výstupu
 <xref:System.Diagnostics.Trace>Třídy a <xref:System.Diagnostics.Debug> poskytují následující metody výstupu:

- Různé `Write` metody, které výstupní informace bez přerušení provádění. Tyto metody nahrazují `Debug.Print` metodu použitou v předchozích verzích Visual Basic.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>a <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> metody, které přeruší spuštění a výstupní informace v případě, že se zadaná podmínka nezdařila. Ve výchozím nastavení `Assert` Metoda zobrazí informace v dialogovém okně. Další informace naleznete v tématu [kontrolní výrazy ve spravovaném kódu](../debugger/assertions-in-managed-code.md).

- <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>Metody a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> , které vždy přeruší spuštění a výstupní informace. Ve výchozím nastavení `Fail` metody zobrazují informace v dialogovém okně.

V okně **výstup** se taky můžou zobrazit informace o:

- Moduly, které ladicí program načetl nebo uvolní.

- Výjimky, které jsou vyvolány.

- Procesy, které se ukončí.

- Vlákna, která se ukončí.

## <a name="see-also"></a>Viz také
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Výstup – okno](../ide/reference/output-window.md)
- [Trasování a instrumentace aplikací](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Typy projektů jazyka C#, F # a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
