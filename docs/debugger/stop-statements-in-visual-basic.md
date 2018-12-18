---
title: Stop – příkazy v jazyce Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74be447f523713cdef9ee5c52876ee0acf4c25b2
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056140"
---
# <a name="stop-statements-in-visual-basic"></a>Příkazy Stop v jazyce Visual Basic
Příkaz jazyka Visual Basic zastavit poskytuje programovací alternativou k nastavení boru přerušení. Když v ladicím programu dojde příkaz Stop, dělí spuštění programu (přejde do režimu přerušení). Stejného efektu pomocí volání do System.Diagnostics.Debugger.Break můžete dosáhnout programátory v jazyce C#.  
  
 Můžete nastavit nebo odebrat příkaz Stop úpravou vašeho zdrojového kódu. Nelze nastavit nebo vymazat příkazech Stop pomocí příkazů ladicího programu, jako byste zarážky.  
  
 Na rozdíl od příkazu End příkaz Stop nemá resetovat proměnné nebo vrátíte do režimu návrhu. Chcete-li pokračovat, spustíte aplikaci v nabídce ladění můžete pokračovat.  
  
 Když spustíte aplikace Visual Basic mimo ladicí program, bude příkaz Stop spuštění ladicího programu Pokud těsně za běhu je povoleno ladění. Pokud těsně za běhu není povoleno ladění, příkaz Stop chová jako by šlo příkazu End ukončení provádění. Žádné QueryUnload nebo uvolnění události dojde, takže je nutné odebrat všechny příkazy Stop z prodejní verze aplikace Visual Basic. Další informace najdete v tématu [ladění JIT](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Abyste se vyhnuli nutnosti odebírání příkazech Stop, můžete použít Podmíněná kompilace:  
  
```cpp
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 Další alternativou je použití příkazu Assert místo příkaz Zastavit. Příkaz Debug.Assert – dělí provádění, pouze pokud je zadaná podmínka není splněná a je automaticky odstraněna při sestavování prodejní verzi. Další informace najdete v tématu [kontrolní výrazy ve spravovaného kódu](../debugger/assertions-in-managed-code.md). Pokud chcete příkazu Assert, který vždy dělí provádění v ladicí verze, můžete provést toto:  
  
```csharp
Debug.Assert(false)  
```  
  
 Další alternativou je ještě použít metodu Debug.Fail:  
  
```csharp
Debug.Fail("a clever output string goes here")  
```  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [C#, F # a typy projektů jazyka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
