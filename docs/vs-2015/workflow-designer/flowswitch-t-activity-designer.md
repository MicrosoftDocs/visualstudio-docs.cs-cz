---
title: Návrhář aktivit &gt; FlowSwitch &lt;T | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 27abb660766a7c04742eca221432af19f05f0d28
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656648"
---
# <a name="flowswitchlttgt-activity-designer"></a>Návrhář aktivity &gt; FlowSwitch &lt;T
Aktivita <xref:System.Activities.Statements.FlowSwitch%601> je podmíněný uzel, který poskytuje větvení pro tok řízení na základě kritéria shody, pokud jsou vyžadovány více než dvě alternativní větve. Pokud větve toku vyžaduje pouze dvě cesty, použijte místo toho <xref:System.Activities.Statements.FlowDecision> aktivitu.

## <a name="the-flowswitcht-activity"></a>Aktivita > FlowSwitch \<T
 Aktivita <xref:System.Activities.Statements.FlowSwitch%601> obsahuje <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, která vrací hodnotu typu *t* (zadanou obecným parametrem) při vyhodnocování. Aktivita také obsahuje sadu <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, která určuje jedinečné mapování z možných výsledků tohoto vyhodnocení na sadu <xref:System.Activities.Statements.FlowNode> objektů. Spouštěný <xref:System.Activities.Statements.FlowNode> je ten, jehož objekt typu *t* odpovídá hodnotě vyhodnoceného <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. V případě, že se nezíská shoda, může být <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> případ (volitelně).

### <a name="using-the-flowswitcht-activity-designer"></a>Použití návrháře aktivit > FlowSwitch \<T
 Návrhář aktivity **FlowSwitch \<T >** lze najít v kategorii **vývojové diagramy** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X.)

 Návrhář aktivity **FlowSwitch \<T >** lze přetáhnout z **panelu nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrch v Návrháři aktivity **vývojového diagramu** . Použijte okno **vybrat typy** , které se zobrazí, chcete-li určit typ (přidružený v kódu s <xref:System.Activities.Statements.FlowSwitch%601> podle jeho obecného parametru) získaného při vyhodnocování <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Tento postup vytvoří <xref:System.Activities.Statements.FlowSwitch%601> aktivitu označenou **přepínačem** v rámci aktivity <xref:System.Activities.Statements.Flowchart>. @No__t_0 lze zadat do pole **výrazu** v okně **vlastnosti** kliknutím na místo, kde text nápovědy říká "zadejte výraz VB".

 Myš nad **FlowSwitch \<T >m** návrháře aktivit a způsobí, že čtvercové popisovače, které se používají k propojení <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, se zobrazí kolem jeho okrajů. Po přetažení návrháře aktivity **FlowSwitch < T \>** a dalších návrhářů aktivit do **vývojového diagramu**se objekty <xref:System.Activities.Activity>, které představují, připravené propojit dohromady, aby určovaly pořadí spouštění. Chcete-li vytvořit jednu z <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> přidružených k <xref:System.Activities.Statements.FlowSwitch%601>, klikněte na jeden z čtvercového táhla na okraji **FlowSwitch \<T >** a přetáhněte ho (tak, že podržíte tlačítko myši) k jednomu z popisovačů, které se zobrazují podobným způsobem kolem Cílová aktivita při umístění ukazatele myši na Návrhář. Po uvolnění tlačítka myši a šipky z **FlowSwitch \<T >** do cílového návrháře se zobrazí zpráva, která představuje tento případ. Výchozí hodnota pro tento případ se zobrazí na šipce a může být upravena v poli **případ** v okně **vlastnosti** .

### <a name="the-flowswitcht-properties"></a>Vlastnosti FlowSwitch \<T >
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.FlowSwitch%601> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Podmínka|Určuje výraz, který se vyhodnocuje, aby se určilo, na který <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> se má přepnout v cestě k provedení.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Určuje jedinečné mapování z možných výsledků získaných z vyhodnocování <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> do sady objektů <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Podmínka|Určuje mapování, pokud vyhodnocení <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> neodpovídá jedné z hodnot obsažených v objektu <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Viz také
 [](../workflow-designer/flowchart-activity-designers.md) Vývojové [vývojové](../workflow-designer/flowchart-activity-designer.md) diagramy [použitím objektu FlowDecision](../workflow-designer/flowdecision-activity-designer.md)