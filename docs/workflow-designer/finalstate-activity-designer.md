---
title: Návrhář postupu provádění – Návrhář aktivity Finalstate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4f49ed7bd2d370f72d8a6be69c28148fbf67e1bf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924340"
---
# <a name="finalstate-activity-designer"></a>Návrhář aktivity FinalState

<xref:System.Activities.Core.Presentation.FinalState> Návrhář slouží k vytvoření <xref:System.Activities.Statements.State> , která ukončí instance počítače stavu.

## <a name="using-the-finalstate-activity-designer"></a>Pomocí aktivity Finalstate

**FinalState** Návrhář slouží k vytvoření <xref:System.Activities.Statements.State> , který byl předem nakonfigurován jako ukončující stav stavového stroje. A <xref:System.Activities.Statements.State> , který je vytvořený pomocí <xref:System.Activities.Core.Presentation.FinalState> má Návrhář aktivity jeho <xref:System.Activities.Statements.State.IsFinal%2A> vlastnost nastavena na hodnotu **true**, nemá žádné <xref:System.Activities.Statements.State.Exit%2A> aktivity a žádné přechody pocházející z něj. Použít <xref:System.Activities.Core.Presentation.FinalState> návrháře aktivit, které chcete přidat <xref:System.Activities.Statements.State> přetáhněte aktivitu, která je předem nakonfigurovaný jako ukončující stav stavového stroje **FinalState** Návrhář aktivity z **stavového stroje**část **nástrojů** a umístěte ho na návrháře postupu provádění. <xref:System.Activities.Core.Presentation.FinalState> Návrhář aktivity může být přetaženy <xref:System.Activities.Statements.StateMachine> a přechody přidat později; nebo přechodu lze vytvořit jako <xref:System.Activities.Core.Presentation.FinalState> Návrhář aktivity se zahodí. Další informace o vytváření přechody, naleznete v tématu [přechod](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Vlastnosti stavu aktivity v Návrháři postupu provádění

V následující tabulce jsou uvedeny vlastnosti, které lze nastavit pomocí <xref:System.Activities.Core.Presentation.FinalState> návrháře a popisuje, jak se používají v návrháři. Některé z těchto vlastností můžete upravovat v mřížce vlastností a některé lze upravit na návrhové ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Určuje popisný název <xref:System.Activities.Statements.State> návrháře aktivit v záhlaví. Výchozí hodnota je **stavu**. Hodnotu lze upravit v mřížce vlastností nebo přímo v hlavičce návrháře aktivit. <xref:System.Activities.Statements.State.DisplayName%2A> Se používá v navigace s popisem cesty, který se zobrazí v horní části návrháře postupu provádění.<br /><br /> I když <xref:System.Activities.Statements.State.DisplayName%2A> není bezpodmínečně nutné, je osvědčeným postupem je použití jednoho.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Určuje akci, která nastane, pokud se tento stav je převeden na. Tuto hodnotu můžete nastavit tak, že přetáhnete aktivity z **nástrojů** a vyřadit ho do <xref:System.Activities.Statements.State.Entry%2A> oddíl stavu.|

## <a name="see-also"></a>Viz také:

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Stav](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)