---
title: 'Postupy: ladění pracovních postupů založených na ASP.NET (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3bed38f5229cb489f663878759517480b48302c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668656"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Postupy: Ladění pracovních postupů založených na technologii ASP.NET (starší verze)
Toto téma popisuje, jak ladit [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] [!INCLUDE[wf](../includes/wf-md.md)] aplikace, které cílí na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] ve starší verzi [!INCLUDE[wfd1](../includes/wfd1-md.md)] .

 Můžete ladit starší pracovní postupy, které jsou spuštěny v ASP.NET nebo starších pracovních postupech, které jsou publikovány jako webová služba, a to připojením k procesu, ve kterém je pracovní postup hostován.

### <a name="to-debug-an-aspnet-based-workflow"></a>Ladění pracovního postupu založeného na ASP.NET

1. Povolte ladění pro aplikaci ASP.NET nastavením **debug = true** v souboru web.config.

2. Nastavte knihovnu pracovního postupu jako spouštěný projekt a nastavte zarážky v pracovním postupu.

3. V poli projekt pracovního postupu zadejte adresu URL výchozí webové stránky – možnost **ladění** **spustit prohlížeč s externí adresou URL** .

4. V nabídce **ladění** vyberte **připojit k procesu** .

5. V seznamu **procesy k dispozici** vyberte proces, který chcete připojit.

     Připojte se k w3wp.exe, webdev. webServer nebo aspnet_wp procesu, ve kterém je pracovní postup hostovaný.

6. Klikněte na tlačítko **Vybrat** vedle do textového pole **připojit k** .

     Zobrazí se dialogové okno **Vybrat typ kódu** .

7. Vyberte možnost **ladit tyto typy kódu** a vyberte **pracovní postup**.

8. Klikněte na **OK**.

9. Klikněte na **připojit**.

10. Otevřete výchozí webovou stránku v prohlížeči a spusťte pracovní postup.

## <a name="see-also"></a>Viz také
 [Vyvolání ladicího programu sady Visual Studio pro programovací model Windows Workflow Foundation (starší verze)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [Postupy: nastavení zarážek v pracovních postupech (starší verze)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [ladění starších verzí pracovních postupů](../workflow-designer/debugging-legacy-workflows.md)