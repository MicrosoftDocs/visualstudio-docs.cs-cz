---
title: 'Postupy: nastavení zarážek v pracovních postupech (starší verze) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 158592ccef331c541bf27494856cfa1314b21f88
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252548"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Postupy: nastavení zarážek v pracovních postupech (starší verze)
Toto téma popisuje, jak nastavit zarážky [!INCLUDE[wf](../includes/wf-md.md)] sestavení aplikace pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Použijte starší [!INCLUDE[wfd2](../includes/wfd2-md.md)] při vaší [!INCLUDE[wf2](../includes/wf2-md.md)] aplikace musí cílit na platformu [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Když použijete starší [!INCLUDE[wfd2](../includes/wfd2-md.md)] v [!INCLUDE[vs2010](../includes/vs2010-md.md)] k sestavení [!INCLUDE[wf2](../includes/wf2-md.md)] aplikace, můžete nastavit zarážky v kódu jazyka C# a Visual Basic stejně jako v sadě Visual Studio. Podle očekávání, zastaví provádění pracovního postupu u každé zarážky, které jste nastavili.  
  
 Zarážka má tři stavy: *čekající*, *vázán*, a *chyba*. Pokud nastavíte zarážku, čeká na vyřízení a je reprezentován ikonou červené prázdný. Při načítání pracovního postupu typu modulu runtime vázán a je reprezentována solid červenou ikonu. Pokud chcete zadat nesprávný formát pro zarážku, jako s názvem aktivita, která není platná, zobrazí se okno aplikace chyba. Zarážka je přidána do okna zarážky, ale je označena s malým "x".  
  
 Pro aktivitu na povrchu návrhu pracovního postupu můžete nastavit zarážky následujícími způsoby:  
  
-   Klikněte pravým tlačítkem na aktivitu a vyberte **zarážku \ vložit zarážku**.  
  
-   Vyberte aktivitu a stiskněte klávesu F9.  
  
-   Vyberte **Nová zarážka** z **ladění** nabídky.  
  
     Tuto možnost můžete použít také pro nastavení nového zarážky během ladění, když se ladicí program zastaví na zarážce.  
  
    > [!NOTE]
    >  Nastavení zarážek v pracovních postupech, vyvolali se nepodporuje.  
  
### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Nastavení zarážky pomocí možnosti Nová zarážka v nabídce ladění  
  
1.  Na **ladění** nabídce vyberte možnost **Nová zarážka**.  
  
2.  Klikněte na tlačítko **zarážku funkce**.  
  
     **Nová zarážka** zobrazí se dialogové okno.  
  
3.  Zadejte název aktivity v **funkce** textového pole s použitím této syntaxe: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.  
  
    > [!NOTE]
    >  Volitelně můžete místo názvu aktivity v **funkce** textového pole, můžete nastavit zarážku tak, že zadáte absolutní cestu aktivity pracovního postupu. Předpokládejme například, že máte řešení pracovního postupu s názvem **WorkflowConsoleApplication1** a pracovní postup v řešení s názvem **Workflow1** , která používá aktivitu volá **Delay1**. Můžete použít název aktivity **Delay1** nebo zadejte cestu jako **Delay1:WorkflowConsoleApplication1.Workflow1** nebo **Delay1:WorkflowConsoleApplication1.Workflow1: { 6614886A-608E-412B-BF98-99FF1559DDDF}**.  
  
4.  Vyberte **použití IntelliSense** zaškrtávací políčko, chcete-li ověřit název funkce.  
  
     Pokud toto políčko není zaškrtnuto, se neprovádí žádné ověření názvu zarážku.  
  
5.  Vyberte **pracovního postupu** z **jazyk** seznamu.  
  
6.  Klikněte na tlačítko **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Ladění starších verzí pracovních postupů](../workflow-designer/debugging-legacy-workflows.md)   
 [Spuštění ladicího programu sady Visual Studio pro programovací model Windows Workflow Foundation (starší verze)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)