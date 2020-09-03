---
title: Návrhář aktivity použitím objektu FlowDecision | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b93d88462d5e3984b06c671455439e9bd2b07c5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656692"
---
# <a name="flowdecision-activity-designer"></a>Návrhář aktivity FlowDecision
<xref:System.Activities.Statements.FlowDecision>Uzel je podmíněný uzel, který poskytuje větev pro tok řízení do jedné ze dvou alternativ na základě toho, zda je splněna zadaná podmínka. Pokud tok vyžaduje více než dvě větve, použijte <xref:System.Activities.Statements.FlowSwitch%601> místo toho.

## <a name="the-flowdecision-node"></a>Uzel použitím objektu FlowDecision
 Tuto možnost použijte <xref:System.Activities.Statements.FlowDecision> , když se tok dá rozvětvit do dvou cest. <xref:System.Activities.Statements.FlowDecision>Uzel má <xref:System.Activities.Statements.FlowDecision.Condition%2A> a <xref:System.Activities.Statements.FlowNode> přidružený ke každému ze dvou možných výsledků: <xref:System.Activities.Statements.FlowDecision.True%2A> nebo <xref:System.Activities.Statements.FlowDecision.False%2A> . <xref:System.Activities.Statements.FlowDecision.Condition%2A>Je vyhodnocena a hodnota tohoto vyhodnocení určuje, který má <xref:System.Activities.Statements.FlowNode> být zpracován v rámci <xref:System.Activities.Statements.Flowchart> .

### <a name="using-the-flowdecision-designer"></a>Použití návrháře použitím objektu FlowDecision
 Návrháře **použitím objektu FlowDecision** lze najít v kategorii **vývojové diagramy** v **sadě nástrojů**, ke které se dostanete kliknutím na kartu **panelu** nástrojů [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně pomocí **panelu nástrojů** v nabídce **zobrazení** nebo kombinací kláves CTRL + ALT + X).

 Návrhář **použitím objektu FlowDecision** lze přetáhnout z **panelu nástrojů** a zrušit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu v Návrháři aktivity **vývojového diagramu** . Tím se <xref:System.Activities.Statements.FlowDecision> v rámci aktivity **Decision** vytvoří označené rozhodnutí <xref:System.Activities.Statements.Flowchart> . Myš nad návrhářem a čtvercové táhlo **true** a **false** pro dvě větve se zobrazí.

 Po přetažení návrháře **použitím objektu FlowDecision** a dalších návrhářů do **vývojového diagramu**lze uzly propojit dohromady, aby bylo možné určit pořadí spouštění. Chcete-li vytvořit propojení mezi zdrojovým uzlem (včetně hodnot **true** a **false** v **použitím objektu FlowDecision**) a cílového uzlu, myši v Návrháři zdrojového uzlu a čtvercového táhla se zobrazí na každé straně. Klikněte na jeden z čtvercových popisovačů a přetáhněte ho tak, že podržíte tlačítko myši na jeden z úchytů, který se zobrazí podobným způsobem kolem cílového uzlu při pohybu myší. Uvolněte tlačítko myši a propojení mezi vytvořením těchto dvou uzlů, které jsou reprezentovány jako šipka od zdrojového návrháře do cílového návrháře.

 Výraz, který uvádí stav, <xref:System.Activities.Statements.FlowDecision.Condition%2A> lze zadat v poli **Podmínka** v okně **vlastnosti** kliknutím na místo, kde text nápovědy říká "zadejte výraz jazyka VB".

### <a name="the-flowdecision-properties"></a>Vlastnosti použitím objektu FlowDecision
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.FlowDecision> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Ano|Podmínka, která určuje, která cesta má řízení toku trvat.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|Ne|Cesta provedená ovládacím prvkem flow, pokud <xref:System.Activities.Statements.FlowDecision.Condition%2A> je splněna.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|Ne|Cesta provedená ovládacím prvkem flow, pokud <xref:System.Activities.Statements.FlowDecision.Condition%2A> není splněna.|

## <a name="see-also"></a>Viz také
 [Flowchart](../workflow-designer/flowchart-activity-designers.md) Vývojové [vývojové](../workflow-designer/flowchart-activity-designer.md) diagramy [FlowSwitch \<T> ](../workflow-designer/flowswitch-t-activity-designer.md)