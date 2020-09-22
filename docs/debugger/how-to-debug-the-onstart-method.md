---
title: Ladění metody OnStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: d695e4d22c728eb256aeb0e1350819ba23b93385
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852371"
---
# <a name="how-to-debug-the-onstart-method"></a>Postupy: Ladění metody OnStart
Službu systému Windows můžete ladit spuštěním služby a připojením ladicího programu k procesu služby. Další informace naleznete v tématu [How to: Debug Application Service Applications](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Chcete-li však ladit <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> metodu služby systému Windows, je nutné spustit ladicí program zevnitř metody.

1. Přidejte volání na <xref:System.Diagnostics.Debugger.Launch%2A> začátek `OnStart()` metody.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Službu spusťte (můžete použít `net start` nebo spustit v okně **služby** ).

    Mělo by se zobrazit dialogové okno podobné následujícímu:

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. Vyberte **Ano, ladit \<service name> .**

4. V okně ladicí program za běhu vyberte verzi sady Visual Studio, kterou chcete použít pro ladění.

    ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")

5. Spustí se nová instance sady Visual Studio a provádění se zastaví v `Debugger.Launch()` metodě.

## <a name="see-also"></a>Viz také
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
