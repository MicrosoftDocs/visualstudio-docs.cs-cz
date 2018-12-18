---
title: Odesílání zpráv do okna výstup | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/08/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02bdd2c6d83e13887a8051ab4101627ba14220fa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724480"
---
# <a name="send-messages-to-the-output-window"></a>Odesílání zpráv do okna výstup

Můžete napsat zpráv za běhu **výstup** pomocí okna <xref:System.Diagnostics.Debug> třídy nebo <xref:System.Diagnostics.Trace> třídy, které jsou součástí z <xref:System.Diagnostics> knihovny tříd. Použití <xref:System.Diagnostics.Debug> třídy, pokud chcete výstup pouze *ladění* verzi aplikace. Použití <xref:System.Diagnostics.Trace> třídy, pokud chcete výstup v obou *ladění* a *vydání* verze.  
  
## <a name="output-methods"></a>Výstup metody  
 <xref:System.Diagnostics.Trace> a <xref:System.Diagnostics.Debug> třídy poskytují metody pro následující výstup:  
  
- Různé `Write` metody, které výstup s informacemi bez narušení provádění. Nahraďte tyto metody `Debug.Print` metodu použitou v předchozích verzích jazyka Visual Basic.  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> a <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> metody, které přeruší informace o spuštění a výstupu, pokud je zadaná podmínka se nezdaří. Ve výchozím nastavení `Assert` metoda zobrazí informace v dialogovém okně. Další informace najdete v tématu [kontrolní výrazy ve spravovaném kódu](../debugger/assertions-in-managed-code.md).  
  
- <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> metody, které vždy přeruší provádění a výstupní informace. Ve výchozím nastavení `Fail` metody zobrazení informací v dialogovém okně.  
  
**Výstup** okna můžete také zobrazit informace o:  
  
- Moduly ladicí program má načten nebo byla uvolněna.  
  
- Výjimky, které jsou vyvolány.  
  
- Procesy, které ukončíte.  
  
- Vlákna, která ukončíte.  
  
## <a name="see-also"></a>Viz také:  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Okno výstup](../ide/reference/output-window.md)   
 [Trasování a instrumentace aplikací](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [C#, F#a typy projektů jazyka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
