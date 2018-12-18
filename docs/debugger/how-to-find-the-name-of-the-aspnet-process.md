---
title: Najít spuštěný proces ASP.NET | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 6bbb2aed6f7218170e26b736d82ba0f3d88b2fae
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751773"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Hledání názvu procesu ASP.NET

Chcete-li ladit průběžný [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace, ladicí program sady Visual Studio musí připojovat k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] podle názvu procesu.

**Chcete-li zjistit, který proces běží aplikace ASP.NET:**

1. Aplikace běžící v sadě Visual Studio, vyberte **ladění** > **připojit k procesu**. 
   
1. V **připojit k procesu** dialogové okno, zadejte názvy z následujícího seznamu první písmena v procesu, nebo zadejte do vyhledávacího pole. Ten, na kterém běží, která je spuštěná aplikace ASP.NET. Připojení k této proces pro ladění aplikace. 
   
    - *W3wp.exe* je služba IIS 6.0 a novějším. 
    - *aspnet_wp.exe* je starší verze služby IIS.
    - *IISExpress.exe* je IISExpress.
    - *DotNet.exe* ASP.NET Core.
    - *Inetinfo.exe* je starší aplikace ASP spuštěné v rámci procesu. 

>[!NOTE]
>Visual Studio 2012 a starších [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kódu lze v systému souborů a spustit na serveru test *WebDev.WebServer.exe* nebo *WebDev.WebServer40.exe*. V takovém případě pro místní ladění připojit k *WebDev.WebServer.exe* nebo *WebDev.WebServer40.exe* místo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu. 

**Viz také:**

 [Připojit ke spuštěnému procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [Předpoklady pro vzdálené ladění webových aplikací](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Požadavky na systém](../debugger/aspnet-debugging-system-requirements.md)   
 [Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)