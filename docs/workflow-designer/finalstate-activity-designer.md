---
title: Návrhář aktivity Návrhář postupu provádění – FinalState
description: Zjistěte, jak můžete pomocí návrháře FinalState vytvořit stav, který ukončuje instanci stavového stroje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2af8887a11b04679789f57f15f32ca03b7b4acf3
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435818"
---
# <a name="finalstate-activity-designer"></a>Návrhář aktivity FinalState

<xref:System.Activities.Core.Presentation.FinalState>Návrhář slouží k vytvoření <xref:System.Activities.Statements.State> , který ukončí instanci stavového stroje.

## <a name="using-the-finalstate-activity-designer"></a>Pomocí návrháře aktivity FinalState

Návrhář **FinalState** slouží k vytvoření a <xref:System.Activities.Statements.State> , který je předem nakonfigurovaný jako ukončovací stav na stavovém stroji. Objekt <xref:System.Activities.Statements.State> , který je vytvořen pomocí <xref:System.Activities.Core.Presentation.FinalState> návrháře aktivit má <xref:System.Activities.Statements.State.IsFinal%2A> vlastnost nastavenou na **hodnotu true** , nemá žádnou <xref:System.Activities.Statements.State.Exit%2A> aktivitu a přechází z něj žádné přechody. Chcete-li použít <xref:System.Activities.Core.Presentation.FinalState> návrháře aktivit k přidání <xref:System.Activities.Statements.State> aktivity, která je předem nakonfigurovaná jako ukončovací stav ve stavovém počítači, přetáhněte návrháře aktivity **FinalState** z oddílu **Stavový počítač** v **sadě nástrojů** a přetáhněte ho do návrháře pracovních postupů. <xref:System.Activities.Core.Presentation.FinalState>Návrhář aktivity může být vyřazen na <xref:System.Activities.Statements.StateMachine> a přechody přidané později. můžete také vytvořit přechod, protože <xref:System.Activities.Core.Presentation.FinalState> Návrhář aktivity je vyřazen. Další informace o vytváření přechodů najdete v tématu [přechod](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Vlastnosti aktivity stavu v Návrhář postupu provádění

V následující tabulce jsou uvedeny vlastnosti, které lze nastavit pomocí <xref:System.Activities.Core.Presentation.FinalState> návrháře, a popisuje, jak se používají v návrháři. Některé z těchto vlastností lze upravit v mřížce vlastností a některé lze upravovat na návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Nepravda|Určuje popisný název <xref:System.Activities.Statements.State> návrháře aktivit v hlavičce. Výchozí hodnota je **State (stav** ). Hodnotu lze upravit v mřížce vlastností nebo přímo v záhlaví návrháře aktivit. <xref:System.Activities.Statements.State.DisplayName%2A>Používá se v navigaci s popisem cesty, které se zobrazí v horní části návrháře pracovních postupů.<br /><br /> I když <xref:System.Activities.Statements.State.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.State.Entry%2A>|Nepravda|Určuje akci, která nastane, když je tento stav převeden na. Tuto hodnotu lze nastavit přetažením aktivity z **panelu nástrojů** a jejím přetažením do <xref:System.Activities.Statements.State.Entry%2A> části stavu.|

## <a name="see-also"></a>Viz také

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Stav](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)