---
title: 'Postupy: nastavení zarážek v pracovních postupech (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 182f28a2b21ae3129ce0d34fae97280ba0a07218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603599"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Postupy: Nastavení zarážek v pracovních postupech (starší verze)
Toto téma popisuje, jak nastavit zarážky v [!INCLUDE[wf](../includes/wf-md.md)] sestavách aplikací pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Použijte starší verze, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Pokud vaše [!INCLUDE[wf2](../includes/wf2-md.md)] aplikace musí cílit na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Když použijete starší verze [!INCLUDE[wfd2](../includes/wfd2-md.md)] v [!INCLUDE[vs2010](../includes/vs2010-md.md)] k sestavení [!INCLUDE[wf2](../includes/wf2-md.md)] aplikace, můžete nastavit zarážky v jazyce C# a Visual Basic kódu jako v sadě Visual Studio. Jak bylo očekáváno, spuštění pracovního postupu se zastaví v každé zarážce, kterou jste nastavili.

 Zarážka má tři stavy: *nevyřízené*, *vázané*a *chybové*. Při nastavení zarážky čeká na vyřízení a je reprezentována červenou červenou ikonou. Když modul runtime načte typ pracovního postupu, bude se jednat o vazbu a bude reprezentován plnou červenou ikonou. Pokud zadáte nesprávný formát pro zarážku, jako u názvu aktivity, který není platný, zobrazí se chybové okno. Zarážka je stále přidána do okna zarážky, ale je označena malým znakem "x".

 Můžete nastavit zarážky u aktivity na návrhové ploše pracovního postupu následujícími způsoby:

- Klikněte pravým tlačítkem na aktivitu a vyberte **zarážku \ Vložit zarážku**.

- Vyberte aktivitu a stiskněte F9.

- V nabídce **ladění** vyberte **Nová zarážka** .

     Tuto možnost lze také použít k nastavení nové zarážky při ladění, když se ladicí program zastaví na zarážce.

    > [!NOTE]
    > Nastavení zarážek u vyvolaných pracovních postupů se nepodporuje.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Nastavení zarážky pomocí možnosti Nová zarážka v nabídce ladění

1. V nabídce **ladění** vyberte **Nová zarážka**.

2. Klikněte na tlačítko **přerušit u funkce**.

     Otevře se dialogové okno **Nová zarážka** .

3. V textovém poli **funkce** zadejte název aktivity pomocí této syntaxe: `QualifiedActivityId[:[FullClassName][:InstanceId]]` .

    > [!NOTE]
    > Volitelně můžete namísto použití názvu aktivity v textovém poli **funkce** nastavit zarážku zadáním absolutní cesty aktivity pracovního postupu. Předpokládejme například, že máte řešení pracovního postupu s názvem **WorkflowConsoleApplication1** a pracovní postup v řešení s názvem **Workflow1** , který používá aktivitu nazvanou **Delay1**. Můžete použít název aktivity **Delay1** nebo zadat cestu jako **Delay1: WorkflowConsoleApplication1. Workflow1** nebo **Delay1: WorkflowConsoleApplication1. Workflow1: {6614886A-608E-412B-BF98-99FF1559DDDF}**.

4. Zaškrtněte políčko **použít technologii IntelliSense** pro ověření názvu funkce.

     Pokud toto políčko není zaškrtnuté, není provedeno ověření názvu zarážky.

5. V seznamu **jazyk** vyberte **pracovní postup** .

6. Klikněte na **OK**.

## <a name="see-also"></a>Viz také
 [Ladění starších pracovních postupů](../workflow-designer/debugging-legacy-workflows.md) [vyvolává ladicí program sady Visual Studio pro programovací model Windows Workflow Foundation (starší verze)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)