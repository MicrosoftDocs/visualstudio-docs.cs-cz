---
title: Příkazy stop v Visual Basic | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f2749ef9a6cfd310da5da832a283b55b6af59a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198892"
---
# <a name="stop-statements-in-visual-basic"></a>Příkazy Stop v jazyce Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Příkaz Visual Basic stop poskytuje programovou alternativu k nastavení zarážky. Když ladicí program nalezne příkaz Stop, přeruší provádění programu (přejde do režimu přerušení). Programátoři v jazyce C# mohou dosáhnout stejného efektu pomocí volání System. Diagnostics. Debugger. Break.  
  
 Příkaz Stop nastavíte nebo odeberete úpravou zdrojového kódu. Příkazy stop nemůžete nastavit ani zrušit pomocí příkazů ladicího programu, stejně jako zarážky.  
  
 Na rozdíl od příkazu end, příkaz Stop neresetuje proměnné nebo se vrátí do režimu návrhu. Kliknutím na pokračovat v nabídce ladění můžete pokračovat v používání aplikace.  
  
 Když spustíte Visual Basic aplikaci mimo ladicí program, příkaz Stop spustí ladicí program, pokud je povoleno ladění za běhu. Pokud ladění za běhu není povoleno, příkaz Stop se chová, jako by šlo o příkaz end, ukončení provádění. Dojde k žádné události QueryUnload ani Unload, takže je nutné odebrat všechny příkazy stop z prodejní verze vaší aplikace Visual Basic. Další informace naleznete v tématu [ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Chcete-li se vyhnout nutnosti odebrat příkazy stop, můžete použít podmíněnou kompilaci:  
  
```  
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 Další alternativou je použití příkazu kontrolního výrazu namísto příkazu stop. Příkaz Debug. Assert přerušuje provádění pouze v případě, že zadaná podmínka není splněna a při sestavení vydané verze je automaticky odebrána. Další informace naleznete v tématu [kontrolní výrazy ve spravovaném kódu](../debugger/assertions-in-managed-code.md). Pokud chcete příkaz Assert, který vždy přeruší provádění v ladicí verzi, můžete to provést:  
  
```  
Debug.Assert(false)  
```  
  
 Ještě další alternativou je použití metody Debug. selhání:  
  
```  
Debug.Fail("a clever output string goes here")  
```  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Typy projektů jazyka C#, F # a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
