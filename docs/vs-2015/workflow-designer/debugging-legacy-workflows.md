---
title: Ladění starších verzí pracovních postupů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 5d835ddc84fae24130035f0664d446a73b7ac3f4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897703"
---
# <a name="debugging-legacy-workflows"></a>Ladění starších verzí pracovních postupů
Pokud používáte starší [!INCLUDE[wfd1](../includes/wfd1-md.md)] v [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] sestavit [!INCLUDE[wf](../includes/wf-md.md)] aplikace, že target.NET rozhraní Framework 3.0 nebo 3.5, můžete ladit vaše pracovní postupy, jako ostatní programy nastavením zarážek, připojení k procesům a kontrole vláken a Zásobník volání. Máte také možnost vzdáleného ladění.  
  
> [!NOTE]
>  Pokud instalaci a odinstalaci na svém počítači více verzí sady Visual Studio, ladění WF3 může selhat s jedním ze dvou následujících možností:  
> 
> - Nejsou vaše zarážky.  
>   -   Zobrazí se následující zpráva:  
> 
>   **Nepodařilo se zahájit ladění na webovém serveru. Ladicí program není správně nainstalován.  Nelze ladit požadovaný typ kódu.  Spusťte instalační program pro nainstalování nebo opravení ladicího programu.**  
> 
>   Pokud některý z těchto scénářů dojde při ladění v rozhraní .NET Framework 3.0 nebo 3.5 pracovních postupů, proveďte opravu instalace sady Visual Studio.  
  
 [!INCLUDE[wf2](../includes/wf2-md.md)] se integruje s následující standardní [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ladění systému windows:  
  
- **Zarážka**: funguje podle očekávání, ale zadejte aktivitu pro název funkce.  
  
- **Zásobník volání**: upravené poskytují přehled aktivit, které jste spustili v instanci pracovního postupu. Položky **zásobník volání** jsou první hloubka vyhledávání provedení aktivity. Klikněte dvakrát na záznam, tím přesuňte fokus na vybranou aktivitou.  
  
- **Vlákna**: poskytuje instance ID instance pracovního postupu, který je právě laděna.  
  
  Visual Studio pro Windows Workflow Foundation nepodporuje následující funkce ladění:  
  
- Podmíněné zarážky na návrhové ploše.  
  
- Rychlé kukátko.  
  
- Nastavení dalšího příkazu.  
  
- Spusťte ke kurzoru.  
  
- Upravit a pokračovat.  
  
- Ladění just-in-time.  
  
- Ladění ve smíšeném režimu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Spuštění ladicího programu sady Visual Studio pro programovací model Windows Workflow Foundation (starší verze)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Zakázání ladicího programu sady Visual Studio pro programovací model Windows Workflow Foundation (starší verze)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Postupy: Ladění pracovních postupů založených na technologii ASP.NET (starší verze)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)  
  
 [Postupy: Nastavení zarážek v pracovních postupech (starší verze)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)  
  
 [Ladění pracovních postupů ze vzdáleného počítače (starší verze)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)  
  
 [Možnosti krokování při ladění (starší verze)](../workflow-designer/debug-stepping-options-legacy.md)  
  
 [Postupy: Změna možností krokování při ladění (starší verze)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)