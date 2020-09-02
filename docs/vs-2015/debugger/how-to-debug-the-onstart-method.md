---
title: 'Postupy: ladění metody OnStart | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 391b906889dcbe422f7ec227b1d375be82e7ac91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700180"
---
# <a name="how-to-debug-the-onstart-method"></a>Postupy: Ladění metody OnStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Službu systému Windows můžete ladit spuštěním služby a připojením ladicího programu k procesu služby. Další informace naleznete v tématu [How to: Debug Application Service Applications](https://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2). Chcete-li však ladit <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> metodu služby systému Windows, je nutné spustit ladicí program zevnitř metody.  
  
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
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
