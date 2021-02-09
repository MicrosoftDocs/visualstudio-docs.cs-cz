---
title: Příkazy stop v Visual Basic | Microsoft Docs
description: Přečtěte si příkaz Visual Basic stop, který poskytuje programovou alternativu k nastavení zarážky v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a17aafd508acd9272e8058ea7ca3ff585a8c0c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904938"
---
# <a name="stop-statements-in-visual-basic"></a>Příkazy Stop v jazyce Visual Basic

Příkaz Visual Basic stop poskytuje programovou alternativu k nastavení zarážky. Když ladicí program nalezne příkaz Stop, přeruší provádění programu (přejde do režimu přerušení). Programátoři v jazyce C# mohou dosáhnout stejného efektu pomocí volání <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> .

Příkaz Stop nastavíte nebo odeberete úpravou zdrojového kódu. Příkazy stop nemůžete nastavit ani zrušit pomocí příkazů ladicího programu, stejně jako zarážky.

Na rozdíl od příkazu end, příkaz Stop neresetuje proměnné nebo se vrátí do režimu návrhu. Kliknutím na pokračovat v nabídce ladění můžete pokračovat v používání aplikace.

Když spustíte Visual Basic aplikaci mimo ladicí program, příkaz Stop spustí ladicí program, pokud je povoleno ladění za běhu. Pokud ladění za běhu není povoleno, příkaz Stop se chová, jako by šlo o příkaz end a ukončí provádění. Dojde k žádné události QueryUnload ani Unload, takže je nutné odebrat všechny příkazy stop z prodejní verze vaší aplikace Visual Basic. Další informace naleznete v tématu [ladění za běhu](just-in-time-debugging-in-visual-studio.md).

 Chcete-li se vyhnout nutnosti odebrat příkazy stop, můžete použít podmíněnou kompilaci:

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

Další alternativou je použití <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> příkazu namísto příkazu stop. <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>Příkaz přeruší provádění pouze v případě, že zadaná podmínka není splněna. <xref:System.Diagnostics.Debug.Assert%2A> příkazy se při sestavení verze vydaných verzí automaticky odeberou. Další informace naleznete v tématu [kontrolní výrazy ve spravovaném kódu](assertions-in-managed-code.md). Pokud chcete <xref:System.Diagnostics.Debug.Assert%2A> příkaz, který vždy přeruší provádění v ladicí verzi, můžete to provést:

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

Ještě další alternativou je použití <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> metody:

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>Viz také

- [Zabezpečení ladicího programu](debugger-security.md)
- [Typy projektů jazyka C#, F# a Visual Basic](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Ladění spravovaného kódu](debugging-managed-code.md)
