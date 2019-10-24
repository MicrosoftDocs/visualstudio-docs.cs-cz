---
title: 'Postupy: ladění metody OnStart | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 107ce6d5ca2b327d77fe588e1ac7ffda10a0a3a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733630"
---
# <a name="how-to-debug-the-onstart-method"></a>Postupy: Ladění metody OnStart
Službu systému Windows můžete ladit spuštěním služby a připojením ladicího programu k procesu služby. Další informace naleznete v tématu [How to: Debug Application Service Applications](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Chcete-li však ladit metodu <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> služby systému Windows, je nutné spustit ladicí program zevnitř metody.

1. Přidejte volání <xref:System.Diagnostics.Debugger.Launch%2A> na začátku `OnStart()`method.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Spusťte službu (můžete použít `net start` a spustit ji v okně **služby** ).

    Mělo by se zobrazit dialogové okno podobné následujícímu:

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. Vyberte **Ano, \<service > název pro ladění.**

4. V okně ladicí program za běhu vyberte verzi sady Visual Studio, kterou chcete použít pro ladění.

    ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")

5. Spustí se nová instance sady Visual Studio a spuštění se zastaví v `Debugger.Launch()` metodě.

## <a name="see-also"></a>Viz také:
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
