---
title: Návrhář postupu provádění - FlowSwitch<T> návrháře aktivit
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 783f3101f567f5fe45a1de24a8dad866ea619a39
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848127"
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch\<T > návrháře aktivit

<xref:System.Activities.Statements.FlowSwitch%601> Aktivita je podmíněné uzel, který poskytuje větvení pro tok řízení založené na shodu kritériu, když se vyžadují více než dvě alternativní větve. Pokud tok větvení vyžaduje pouze dvě cesty, použijte <xref:System.Activities.Statements.FlowDecision> aktivity místo.

## <a name="the-flowswitcht-activity"></a>FlowSwitch\<T > aktivity

<xref:System.Activities.Statements.FlowSwitch%601> Obsahuje aktivity <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> , která vrátí hodnotu typu *T* (určeného obecný parametr) při vyhodnocování. Aktivita také obsahuje sadu <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, která určuje jedinečný mapování z možných výsledků vyhodnocení na sadu <xref:System.Activities.Statements.FlowNode> objekty. <xref:System.Activities.Statements.FlowNode> Proveden, je ten, jehož objekt typu *T* odpovídá hodnotě vyhodnocené <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. A <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> případu (volitelně) lze zadat pro případ, ve kterém se získá žádná shoda.

### <a name="using-the-flowswitcht-activity-designer"></a>Použití FlowSwitch\<T > návrháře aktivit

**FlowSwitch\<T >** návrháře aktivit najdete v **vývojový diagram** kategorii **nástrojů**, který přistupuje po kliknutí **Nástrojů** karty na levé straně návrháře postupu provádění. Můžete také vybrat **nástrojů** z **zobrazení** nabídky nebo stisknutím klávesy **Ctrl**+**Alt** + **X**.

**FlowSwitch\<T >** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění v rámci **vývojový diagram** Návrhář aktivity. Použití **vyberte typy** okno zobrazující určení typu (přidružená v kódu pomocí <xref:System.Activities.Statements.FlowSwitch%601> podle jeho obecných parametrů) získané z vyhodnocení <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Tato procedura vytváří <xref:System.Activities.Statements.FlowSwitch%601> aktivity označené jako **přepínač** v rámci <xref:System.Activities.Statements.Flowchart> aktivity. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Lze napsat **výraz** pomocí boxingu **vlastnosti** okno kliknutím, kde text nápovědy říká "Zadejte výrazu jazyka VB".

Najedete myší **FlowSwitch\<T >** Návrhář aktivity způsobit Čtvereček obslužné rutiny, které se používají k propojení <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> kolem okraje. Po přetažení **FlowSwitch < T\>**  návrháře aktivit a jiné návrháře aktivit do **vývojový diagram**, <xref:System.Activities.Activity> objekty, které představují jsou připraveny k propojení Chcete-li určit pořadí provádění. Vytvořit jeden z <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> přidružené <xref:System.Activities.Statements.FlowSwitch%601>, klikněte na některou čtverec případu obslužné rutiny na hraničních **FlowSwitch < T\>**  a přetáhněte ji do jednoho z úchytů (podržením tlačítka myši) který se zobrazí podobným způsobem kolem cílová aktivita po umístění ukazatele myši nad jeho návrháře. Uvolněte tlačítko myši a šipky z **FlowSwitch < T\>**  na cílovém návrháři se zobrazí představující tento případ. Výchozí hodnota pro tento případ se zobrazí na šipce a upravovat v **případ** pomocí boxingu **vlastnosti** okna.

### <a name="the-flowswitcht-properties"></a>FlowSwitch\<T > Vlastnosti

Následující tabulka ukazuje <xref:System.Activities.Statements.FlowSwitch%601> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností nebo na plochu návrháře.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Hodnota TRUE|Určuje výraz, který je vyhodnocován pro určení, které <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> přejděte do cesty spuštění.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Určuje jedinečný mapování z možných výsledků získaných z vyhodnocení <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> na sadu <xref:System.Activities.Statements.FlowNode> objekty.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Hodnota TRUE|Určuje mapování při vyhodnocení <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> se neshoduje s některou z hodnot součástí <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> objektu.|

## <a name="see-also"></a>Viz také:

- [Vývojový diagram](../workflow-designer/flowchart-activity-designers.md)
- [Vývojový diagram](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)