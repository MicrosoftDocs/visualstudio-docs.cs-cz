---
title: Nastavení názvu vlákna ve spravovaném kódu | Microsoft Docs
description: Nastavte název vlákna ve spravovaném kódu během ladění vícevláknových aplikací v sadě Visual Studio. Pojmenování vláken slouží k udržení přehledu o vláknech v okně vláken.
ms.custom: SEO-VS-2020
ms.date: 04/27/2017
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3defa5eaee2aafabcb4cf890516f7c78be47b1e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915763"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Postupy: Nastavení názvu vlákna ve spravovaném kódu
Pojmenování vlákna je možné v libovolné verzi sady Visual Studio. Pojmenovávání vláken je užitečné pro udržení přehledu o vláknech v okně **vláken** .

 Chcete-li nastavit název vlákna ve spravovaném kódu, použijte <xref:System.Threading.Thread.Name%2A> vlastnost.

## <a name="example"></a>Příklad

```csharp
public class Needle
{
    // This method will be called when the thread is started.
    public void Baz()
    {
        Console.WriteLine("Needle Baz is running on another thread");
    }
}

public void Main()
{
    Console.WriteLine("Thread Simple Sample");
    Needle oNeedle = new Needle();
    // Create a Thread object.
    System.Threading.Thread oThread = new System.Threading.Thread(oNeedle.Baz);
    // Set the Thread name to "MyThread".
    oThread.Name = "MyThread";
    // Starting the thread invokes the ThreadStart delegate
    oThread.Start();
}
```

```VB
Public Class Needle
    ' This method will be called when the thread is started.
    Sub Baz()
        Console.WriteLine("Needle Baz is running on another thread")
    End Sub
End Class

Sub Main()
    Console.WriteLine("Thread Simple Sample")
    Dim oNeedle As New Needle()
   ' Create a Thread object.
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)
    ' Set the Thread name to "MyThread".
    oThread.Name = "MyThread"
    ' Starting the thread invokes the ThreadStart delegate
    oThread.Start()
End Sub
```

## <a name="see-also"></a>Viz také
- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Postupy: Nastavení názvu vlákna v nativním kódu](../debugger/how-to-set-a-thread-name-in-native-code.md)