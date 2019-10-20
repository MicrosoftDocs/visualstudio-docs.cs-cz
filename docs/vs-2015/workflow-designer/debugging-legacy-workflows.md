---
title: Ladění starších verzí pracovních postupů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ae0a08e1623e1b90046d164d8bfe04eaf67229
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656868"
---
# <a name="debugging-legacy-workflows"></a>Ladění starších verzí pracovních postupů
Pokud používáte starší [!INCLUDE[wfd1](../includes/wfd1-md.md)] v [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] k sestavování [!INCLUDE[wf](../includes/wf-md.md)] aplikací, které target.NET Framework 3,0 nebo 3,5, můžete ladit pracovní postupy stejným způsobem jako jakýkoli jiný program nastavením zarážek, připojením k procesům a prozkoumáním vláken a zásobníku volání. Máte také možnost ladění vzdáleně.

> [!NOTE]
> Pokud je v počítači nainstalováno a odinstalováno více verzí sady Visual Studio, ladění WF3 může selhat s jednou z následujících dvou možností:
>
> - Vaše zarážky nejsou k dispozice.
>   - Zobrazí se následující zpráva:
>
>   **Nelze spustit ladění na webovém serveru. Ladicí program není správně nainstalován.  Nelze ladit požadovaný typ kódu.  Spusťte instalační program a nainstalujte nebo opravte ladicí program.**
>
>   Pokud při ladění pracovních postupů .NET Framework 3,0 nebo 3,5 dojde k některému z těchto scénářů, proveďte opravu instalace sady Visual Studio.

 [!INCLUDE[wf2](../includes/wf2-md.md)] se integruje s následujícími standardními okny [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ladění:

- **Zarážka**: funguje podle očekávání, ale zadáte aktivitu pro název funkce.

- **Zásobník volání**: upraveno tak, aby poskytovalo osnovu aktivit, které byly spuštěny v instanci pracovního postupu. Položky v okně **zásobník volání** jsou hloubkovým vyhledáváním provádění aktivit. Dvojitým kliknutím na položku můžete umístit fokus na vybranou aktivitu.

- **Vlákna**: poskytuje ID instance instance pracovního postupu, která se právě ladí.

  Visual Studio for programovací model Windows Workflow Foundation nepodporuje následující funkce ladění:

- Podmíněné zarážky na návrhové ploše.

- QuickWatch.

- Nastavit další příkaz

- Spustit ke kurzoru.

- Upravit a pokračovat.

- Ladění za běhu.

- Ladění ve smíšeném režimu.

## <a name="in-this-section"></a>V tomto oddílu
 [Spuštění ladicího programu sady Visual Studio pro programovací model Windows Workflow Foundation (starší verze)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Zakázání ladicího programu sady Visual Studio pro programovací model Windows Workflow Foundation (starší verze)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Postupy: Ladění pracovních postupů založených na technologii ASP.NET (starší verze)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)

 [Postupy: Nastavení zarážek v pracovních postupech (starší verze)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)

 [Ladění pracovních postupů ze vzdáleného počítače (starší verze)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)

 [Možnosti krokování při ladění (starší verze)](../workflow-designer/debug-stepping-options-legacy.md)

 [Postupy: Změna možností krokování při ladění (starší verze)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)