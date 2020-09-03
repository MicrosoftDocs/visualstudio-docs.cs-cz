---
title: Najít spuštěný proces ASP.NET | Microsoft Docs
ms.date: 11/04/2018
ms.topic: how-to
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: c14067d58289dd0b41fa526937a0553c10934ea7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85349604"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Hledání názvu procesu ASP.NET

Chcete-li ladit spuštěnou [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikaci, musí být ladicí program sady Visual Studio připojen k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu podle názvu.

**Zjistit, na kterém procesu běží aplikace ASP.NET:**

1. V aplikaci spuštěné v aplikaci Visual Studio vyberte **ladit**  >  **připojit k procesu**.

1. V dialogovém okně **připojit k procesu** zadejte první písmena názvů procesů z následujícího seznamu nebo je zadejte do vyhledávacího pole. Ten, který je spuštěný, je ten, který spouští aplikaci ASP.NET. Připojte se k tomuto procesu pro ladění aplikace.

    - *w3wp.exe* je IIS 6,0 a novější.
    - *aspnet_wp.exe* je dřívější verze služby IIS.
    - *iisexpress.exe* je IISExpress.
    - *dotnet.exe* je ASP.NET Core.
    - *inetinfo.exe* jsou starší aplikace ASP spuštěné v procesu.

>[!NOTE]
>Visual Studio 2012 a starší [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kód mohou být v systému souborů a spuštěny na testovacím serveru *WebDev.WebServer.exe* nebo *WebDev.WebServer40.exe*. V tomto případě se k místnímu ladění připojí místo procesu *WebDev.WebServer.exe* nebo *WebDev.WebServer40.exe* [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

**Viz také:**

- [Připojit ke spuštěnému procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Předpoklady pro vzdálené ladění webových aplikací](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Požadavky na systém](../debugger/aspnet-debugging-system-requirements.md)
- [Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)