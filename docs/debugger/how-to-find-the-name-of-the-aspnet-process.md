---
title: Najít spuštěný proces ASP.NET | Microsoft Docs
ms.date: 11/04/2018
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 54aa98dd238d7a78e4ae89af05dceae0f9911478
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187653"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Hledání názvu procesu ASP.NET

Chcete-li ladit běžící aplikaci [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], ladicí program sady Visual Studio se musí připojit k procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] podle názvu.

**Zjistit, na kterém procesu běží aplikace ASP.NET:**

1. V aplikaci, která běží, vyberte v aplikaci Visual Studio možnost **ladění** > **připojit k procesu**.

1. V dialogovém okně **připojit k procesu** zadejte první písmena názvů procesů z následujícího seznamu nebo je zadejte do vyhledávacího pole. Ten, který je spuštěný, je ten, který spouští aplikaci ASP.NET. Připojte se k tomuto procesu pro ladění aplikace.

    - *W3wp. exe* je IIS 6,0 a novější.
    - program *Aspnet_wp. exe* je dřívější verze služby IIS.
    - *IISExpress. exe* je IISExpress.
    - *dotnet. exe* je ASP.NET Core.
    - *Inetinfo. exe* je starší aplikace ASP běžící v procesu.

>[!NOTE]
>Visual Studio 2012 a starší [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kódu mohou být v systému souborů a spuštěny na testovacím serveru *webdev. webServer. exe* nebo *webdev. WebServer40. exe*. V tomto případě pro místní ladění připojte k *webdev. webServer. exe* nebo *webdev. WebServer40. exe* místo procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

**Viz také:**

- [Připojit ke spuštěnému procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Předpoklady pro vzdálené ladění webových aplikací](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Požadavky na systém](../debugger/aspnet-debugging-system-requirements.md)
- [Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)