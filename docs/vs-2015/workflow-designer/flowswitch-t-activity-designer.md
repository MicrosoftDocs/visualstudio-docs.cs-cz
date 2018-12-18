---
title: FlowSwitch&lt;T&gt; Návrhář aktivity | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ed39806fdca8eec3deccf5383c2386d07f0af929
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254748"
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch&lt;T&gt; návrháře aktivit
<xref:System.Activities.Statements.FlowSwitch%601> Aktivita je podmíněné uzel, který poskytuje větvení pro tok řízení založené na shodu kritériu, když se vyžadují více než dvě alternativní větve. Pokud tok větvení vyžaduje pouze dvě cesty, použijte <xref:System.Activities.Statements.FlowDecision> aktivity místo.  
  
## <a name="the-flowswitcht-activity"></a>FlowSwitch\<T > aktivity  
 <xref:System.Activities.Statements.FlowSwitch%601> Obsahuje aktivity <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> , která vrátí hodnotu typu *T* (určeného obecný parametr) při vyhodnocování. Aktivita také obsahuje sadu <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, která určuje jedinečný mapování z možných výsledků vyhodnocení na sadu <xref:System.Activities.Statements.FlowNode> objekty. <xref:System.Activities.Statements.FlowNode> Proveden, je ten, jehož objekt typu *T* odpovídá hodnotě vyhodnocené <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. A <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> případu (volitelně) lze zadat pro případ, ve kterém se získá žádná shoda.  
  
### <a name="using-the-flowswitcht-activity-designer"></a>Použití FlowSwitch\<T > návrháře aktivit  
 **FlowSwitch\<T >** návrháře aktivit najdete v **vývojový diagram** kategorii **nástrojů**, který přistupuje po kliknutí **Nástrojů** karty na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte možnost **nástrojů** z **zobrazení** nabídky nebo CTRL + ALT + X.)  
  
 **FlowSwitch\<T >** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřazené k [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochy v rámci **vývojový diagram** Návrhář aktivity. Použití **vyberte typy** okno zobrazující určení typu (přidružená v kódu pomocí <xref:System.Activities.Statements.FlowSwitch%601> podle jeho obecných parametrů) získané z vyhodnocení <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Tato procedura vytváří <xref:System.Activities.Statements.FlowSwitch%601> aktivity označené jako **přepínač** v rámci <xref:System.Activities.Statements.Flowchart> aktivity. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Lze napsat **výraz** pomocí boxingu **vlastnosti** okno kliknutím, kde text nápovědy říká "Zadejte výrazu jazyka VB".  
  
 Najedete myší **FlowSwitch\<T >** Návrhář aktivity způsobit Čtvereček obslužné rutiny, které se používají k propojení <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> kolem okraje. Po přetažení **FlowSwitch < T\>**  návrháře aktivit a jiné návrháře aktivit do **vývojový diagram**, <xref:System.Activities.Activity> objekty, které představují jsou připraveny k propojení Chcete-li určit pořadí provádění. Vytvořit jeden z <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> přidružené <xref:System.Activities.Statements.FlowSwitch%601>, klikněte na některou čtverec případu obslužné rutiny na hraničních **FlowSwitch\<T >** a přetáhněte ji do jednoho z úchytů (podržením tlačítka myši) který se zobrazí podobným způsobem kolem cílová aktivita po umístění ukazatele myši nad jeho návrháře. Uvolněte tlačítko myši a šipky z **FlowSwitch\<T >** na cílovém návrháři se zobrazí představující tento případ. Výchozí hodnota pro tento případ se zobrazí na šipce a upravovat v **případ** pomocí boxingu **vlastnosti** okna.  
  
### <a name="the-flowswitcht-properties"></a>FlowSwitch\<T > Vlastnosti  
 Následující tabulka ukazuje <xref:System.Activities.Statements.FlowSwitch%601> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností nebo na plochu návrháře.  
  
|Název vlastnosti|Požadováno|Použití|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Hodnota TRUE|Určuje výraz, který je vyhodnocován pro určení, které <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> přejděte do cesty spuštění.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Určuje jedinečný mapování z možných výsledků získaných z vyhodnocení <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> na sadu <xref:System.Activities.Statements.FlowNode> objekty.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Hodnota TRUE|Určuje mapování při vyhodnocení <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> se neshoduje s některou z hodnot součástí <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> objektu.|  
  
## <a name="see-also"></a>Viz také  
 [Vývojový diagram](../workflow-designer/flowchart-activity-designers.md)   
 [Vývojový diagram](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)