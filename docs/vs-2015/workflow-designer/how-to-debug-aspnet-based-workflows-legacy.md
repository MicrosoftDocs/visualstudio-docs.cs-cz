---
title: 'Postupy: ladění založených na technologii ASP.NET pracovních postupů (starší verze) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b9da40b0b40216fc36ea45b199ecde9c6dc4a89d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236883"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Postupy: ladění založených na technologii ASP.NET pracovních postupů (starší verze)
Toto téma popisuje, jak ladit [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]– na základě [!INCLUDE[wf](../includes/wf-md.md)] aplikací určených pro buď [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] ve starší [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
 Můžete ladit starších verzí pracovních postupů, které jsou spuštěny v technologii ASP.NET nebo starších verzí pracovních postupů, které jsou zveřejněné jako webovou službu pomocí připojení k procesu, ve kterém je hostovaný pracovní postup.  
  
### <a name="to-debug-an-aspnet-based-workflow"></a>Chcete-li ladit pracovních postupů založených na technologii ASP.NET  
  
1.  Povolit ladění pro aplikace ASP.NET tak, že nastavíte **ladění = true** v souboru web.config.  
  
2.  Nastavit jako spouštěný projekt knihovny pracovních postupů a nastavení zarážek v pracovním postupu.  
  
3.  Zadejte adresu URL výchozí webová stránka ve vlastnostech projektu pracovního postupu **ladění** možnost **spuštění prohlížeče s externí adresa URL** textového pole.  
  
4.  Vyberte **připojit k procesu** na **ladění** nabídky.  
  
5.  Vyberte proces pro připojení z **procesy k dispozici** seznamu.  
  
     Připojte k procesu w3wp.exe, webdev.webserver nebo aspnet_wp, ve kterém je hostovaný pracovní postup.  
  
6.  Klikněte na tlačítko **vyberte** vedle **připojit k** textového pole.  
  
     **Vybrat typ kódu** zobrazí se dialogové okno.  
  
7.  Vyberte **ladit tyto typy kódu** a vyberte **pracovního postupu**.  
  
8.  Klikněte na tlačítko **OK**.  
  
9. Klikněte na tlačítko **připojit**.  
  
10. Otevřít výchozí webovou stránku v prohlížeči a spusťte pracovní postup.  
  
## <a name="see-also"></a>Viz také  
 [Vyvolání ladicího programu sady Visual Studio pro Windows Workflow Foundation (starší verze)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Postupy: nastavení zarážek v pracovních postupech (starší verze)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Ladění starších verzí pracovních postupů](../workflow-designer/debugging-legacy-workflows.md)