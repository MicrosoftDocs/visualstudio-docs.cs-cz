---
title: Ladění metody OnStart | Microsoft Docs
description: Naučte se ladit metodu OnStart služby Windows v aplikaci Visual Studio – spuštěním ladicího programu zevnitř metody.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 51096d7a47de80be7434659936165ba0a29f7c67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899283"
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

    ![Snímek obrazovky dialogového okna pro ladění za běhu sady Visual Studio, které zobrazuje neošetřenou výjimku .NET Framework nastaly v WindowsService-Asis.exe.](../debugger/media/onstartdebug.png)

3. Vyberte **Ano, ladit \<service name> .**

4. V okně ladicí program za běhu vyberte verzi sady Visual Studio, kterou chcete použít pro ladění.

    ![Snímek obrazovky okna programu pro ladění za běhu sady Visual Studio s vybranou možností nová instance Microsoft Visual Studio 2015 v seznamu možných ladicích programů.](../debugger/media/justintimedebugger.png)

5. Spustí se nová instance sady Visual Studio a provádění se zastaví v `Debugger.Launch()` metodě.

## <a name="see-also"></a>Viz také
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
