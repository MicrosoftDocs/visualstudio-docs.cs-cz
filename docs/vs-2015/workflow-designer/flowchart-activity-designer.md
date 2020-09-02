---
title: Návrhář aktivity vývojového diagramu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a85efea49d641fa54774c1428d15f7d8218ca53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656711"
---
# <a name="flowchart-activity-designer"></a>Návrhář aktivity Flowchart
<xref:System.Activities.Statements.Flowchart>Aktivita se používá k vytváření pracovních postupů, které definují a spravují složité ovládací prvky toku. <xref:System.Activities.Statements.Flowchart>Může být vytvořen buď v kódu, nebo pomocí [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Toto téma popisuje [!INCLUDE[wfd2](../includes/wfd2-md.md)] prostředí. [!INCLUDE[wfd1](../includes/wfd1-md.md)]Návrhář aktivity pracovního postupu umožňuje vývojářům přirozeným způsobem vytvářet pracovní postupy.

## <a name="the-flowchart-activity"></a>Aktivita vývojového diagramu
 <xref:System.Activities.Statements.Flowchart>Určuje jedinečný <xref:System.Activities.Statements.Flowchart.StartNode%2A> , který se spustí při spuštění pracovního postupu a používá síť propojenou <xref:System.Activities.Statements.Flowchart.Nodes%2A> k vytvoření libovolných smyček nebo k překonání toku provádění na kdekoli jinde v pracovním postupu v daném čase.

### <a name="using-the-flowchart-activity-designer"></a>Pomocí návrháře aktivit vývojového diagramu
 Návrhář aktivity **vývojového diagramu** se dá najít v kategorii **vývojové diagramy** na **panelu nástrojů**, ke které se dostanete tak, že kliknete na kartu **panel nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).)

 Návrhář aktivity **vývojového diagramu** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, ať jsou obvykle umístěna návrháři aktivit, buď jako kořenová aktivita, nebo jako podřízený objekt jiné aktivity toku řízení. Pokud je Návrhář aktivity **vývojového diagramu** vyřazen na prázdné [!INCLUDE[wfd2](../includes/wfd2-md.md)] ploše, vytvoří <xref:System.Activities.Statements.Flowchart> aktivitu, která se ve výchozím nastavení projeví v rozšířeném zobrazení, ve kterém je počáteční uzel, který iniciuje spuštění, reprezentován zelenou kuličkou. Pokud je Návrhář aktivity **vývojového diagramu** vyřazen do jiné aktivity toku řízení, zobrazí se v minimalizovaném zobrazení, které lze rozšířit dvojitým kliknutím na Návrhář aktivity **vývojového diagramu** . Jakékoli aktivity v **sadě nástrojů** lze přetáhnout přímo do návrháře aktivit **vývojového diagramu** , včetně dalších aktivit toku řízení.

 Po přetahování různých návrhářů aktivit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plátno <xref:System.Activities.Activity> lze objekty, které představují, propojit společně a určit pořadí spouštění. Chcete-li vytvořit propojení mezi zdrojovou aktivitou a cílovou aktivitou, na každé straně se zobrazí ukazatel myši nad návrhářem zdrojové aktivity a čtvercových popisovačů. Klikněte na jeden z čtvercových popisovačů a přetáhněte ho podržením tlačítka myši na jeden z úchytů, který se zobrazí podobným způsobem kolem cílové aktivity při umístění ukazatele myši myší. Uvolněte tlačítko myši a vytvoří se propojení mezi dvěma aktivitami, které jsou reprezentovány jako šipka od návrháře zdrojového kódu do cílového návrháře.

### <a name="flowchart-activity-properties"></a>Vlastnosti aktivity vývojového diagramu
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Flowchart> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje zobrazovaný název návrháře aktivit v hlavičce. Výchozí hodnota je vývojový diagram. Hodnotu lze upravit v okně **vlastnosti** nebo přímo v hlavičce návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|Ne|Kolekce proměnných, které jsou vymezeny v rámci této <xref:System.Activities.Statements.Flowchart> složky ke sdílení stavu napříč svými podřízenými aktivitami.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|Ne|<xref:System.Activities.Statements.FlowNode>, Který se spustí při <xref:System.Activities.Statements.Flowchart> spuštění.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|Ne|Obsahuje kolekci <xref:System.Activities.Statements.FlowNode> objektů v <xref:System.Activities.Statements.Flowchart> .|

## <a name="see-also"></a>Viz také
 [FlowSwitch \<T> ](../workflow-designer/flowswitch-t-activity-designer.md) [vývojového diagramu](../workflow-designer/flowchart-activity-designers.md) [použitím objektu FlowDecision](../workflow-designer/flowdecision-activity-designer.md)