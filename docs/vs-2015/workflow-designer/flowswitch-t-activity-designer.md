---
title: '&lt; &gt; Návrhář aktivity FlowSwitch T | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656648"
---
# <a name="flowswitchlttgt-activity-designer"></a>&lt; &gt; Návrhář aktivity FlowSwitch T
<xref:System.Activities.Statements.FlowSwitch%601>Aktivita je podmíněný uzel, který poskytuje větvení pro tok řízení na základě kritéria shody, pokud jsou vyžadovány více než dvě alternativní větve. Pokud větve toku vyžaduje pouze dvě cesty, použijte <xref:System.Activities.Statements.FlowDecision> místo toho aktivitu.

## <a name="the-flowswitcht-activity"></a>Aktivita FlowSwitch \<T>
 <xref:System.Activities.Statements.FlowSwitch%601>Aktivita obsahuje objekt <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> , který vrací hodnotu typu *T* (zadanou obecným parametrem) při vyhodnocování. Aktivita obsahuje také sadu <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> , která určuje jedinečné mapování z možných výsledků tohoto vyhodnocení na sadu <xref:System.Activities.Statements.FlowNode> objektů. <xref:System.Activities.Statements.FlowNode>Spustí se ten, jehož objekt typu *T* odpovídá hodnotě vyhodnocené <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . <xref:System.Activities.Statements.FlowSwitch%601.Default%2A>Případ může (volitelně) být k dispozici pro případ, kdy se nezíská shoda.

### <a name="using-the-flowswitcht-activity-designer"></a>Pomocí \<T> Návrháře aktivity FlowSwitch
 Návrhář **aktivity \<T> FlowSwitch** lze najít v kategorii **vývojové diagramy** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář **aktivity \<T> FlowSwitch** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu v Návrháři aktivity **vývojového diagramu** . Použijte okno **vybrat typy** , které se zobrazí, chcete-li určit typ (přidružený v kódu pomocí <xref:System.Activities.Statements.FlowSwitch%601> jeho obecného parametru) získaného z vyhodnocení <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Tento postup vytvoří <xref:System.Activities.Statements.FlowSwitch%601> aktivitu označenou **přepínačem** v rámci <xref:System.Activities.Statements.Flowchart> aktivity. Typ <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> lze zadat v poli **výrazu** v okně **vlastnosti** kliknutím na místo, kde text nápovědy říká "zadejte výraz VB".

 Myš nad Návrhář **aktivity \<T> FlowSwitch** , která způsobí, že čtvercové popisovače, které se použijí k propojení, se <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> zobrazí kolem jeho okrajů. Po přetažení návrháře aktivity **FlowSwitch \><T** a dalších návrhářů aktivit do tohoto **vývojového diagramu** <xref:System.Activities.Activity> jsou objekty, které představují, připravené propojit dohromady, aby určovaly pořadí spouštění. Pokud chcete vytvořit jednu z <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> přidružených k <xref:System.Activities.Statements.FlowSwitch%601> , klikněte na jeden z čtvercového táhla na okraji **FlowSwitch \<T> ** a přetáhněte ho (podržením tlačítka myši) k jednomu z popisovačů, které se zobrazí podobným způsobem kolem cílové aktivity, když ukazatel myši setrvá na návrháři. Po uvolnění tlačítka myši a šipky z **FlowSwitch \<T> ** do cílového návrháře se zobrazí reprezentace tohoto případu. Výchozí hodnota pro tento případ se zobrazí na šipce a může být upravena v poli **případ** v okně **vlastnosti** .

### <a name="the-flowswitcht-properties"></a>Vlastnosti FlowSwitch \<T>
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.FlowSwitch%601> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Ano|Určuje výraz, který je vyhodnocován pro určení, který z <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> přepínačů má být v cestě k provedení přepnut.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Ne|Určuje jedinečné mapování z možných výsledků získaných z vyhodnocení <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> do sady <xref:System.Activities.Statements.FlowNode> objektů.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Ano|Určuje mapování, pokud vyhodnocení neodpovídá <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> jedné z hodnot obsažených v <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> objektu.|

## <a name="see-also"></a>Viz také
 [Flowchart](../workflow-designer/flowchart-activity-designers.md) Vývojové [vývojové](../workflow-designer/flowchart-activity-designer.md) diagramy [použitím objektu FlowDecision](../workflow-designer/flowdecision-activity-designer.md)