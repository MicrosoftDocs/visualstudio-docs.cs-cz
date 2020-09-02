---
title: Diagnostické zprávy v okno Výstup | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.output
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60f8da2430e1c84af3c26be31c6de561291c8c6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695299"
---
# <a name="diagnostic-messages-in-the-output-window"></a>Diagnostické zprávy v okně Výstup
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete psát zprávy za běhu do okna výstup pomocí třídy ladění nebo třídy trasování, která je součástí <xref:System.Diagnostics> knihovny tříd. Třídu Debug použijte, pokud je výstup pouze v ladicí verzi programu. Třídu Trace použijte, pokud chcete výstup v ladicí verzi i ve verzi Release.  
  
## <a name="output-methods"></a>Metody výstupu  
 <xref:System.Diagnostics.Trace>Třídy a <xref:System.Diagnostics.Debug> poskytují následující metody výstupu:  
  
- Různé `Write` metody, které výstupní informace bez přerušení provádění. Tyto metody nahrazují `Debug.Print` metodu použitou v předchozích verzích Visual Basic.  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> a <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> metody, které přeruší provádění a vytvoří výstup informací v případě, že se zadaná podmínka nezdařila. Ve výchozím nastavení `Assert` Metoda zobrazí informace v dialogovém okně. Další informace naleznete v tématu [kontrolní výrazy ve spravovaném kódu](../debugger/assertions-in-managed-code.md).  
  
- <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>Metody a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> , které vždy přerušují provádění a výstupy informací. Ve výchozím nastavení `Fail` metody zobrazují informace v dialogovém okně.  
  
  Kromě programu z aplikace může okno **výstup** zobrazit informace o:  
  
- Moduly, které ladicí program načetl nebo uvolní.  
  
- Výjimky, které jsou vyvolány.  
  
- Procesy, které se ukončí.  
  
- Vlákna, která se ukončí.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [okno Výstup](../ide/reference/output-window.md)   
 [Trasování a instrumentace aplikací](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [Úvod do instrumentace a trasování](https://msdn.microsoft.com/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [Typy projektů jazyka C#, F # a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
