---
title: Návrhář aktivity Návrhář postupu provádění – stav
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: f1a95808ec19edba01b266ccd280603bcc4321dc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593145"
---
# <a name="state-activity-designer"></a>Návrhář aktivity State

<xref:System.Activities.Statements.State> představuje stav, ve kterém může být Stavový počítač v.

## <a name="using-the-state-activity-designer"></a>Použití návrháře aktivity stavu

Chcete-li přidat <xref:System.Activities.Statements.State> k pracovnímu postupu, přetáhněte návrháře aktivity **stavu** z části **Stavový počítač** v **panelu nástrojů** a přetáhněte jej na <xref:System.Activities.Statements.StateMachine> aktivitu na Návrhář postupu provádění ploše. <xref:System.Activities.Statements.State> aktivitu lze přetáhnout na <xref:System.Activities.Statements.StateMachine> a přechody přidané později. nebo je možné vytvořit přechod, protože aktivita <xref:System.Activities.Statements.State> je vyřazena. Chcete-li přidat aktivitu <xref:System.Activities.Statements.State> a vytvořit přechod v jednom kroku, přetáhněte aktivitu **stavu** z části **Stavový počítač** v **sadě nástrojů** a umístěte ji do jiného stavu v Návrháři postupu. Když je přetažené <xref:System.Activities.Statements.State> nad jiným <xref:System.Activities.Statements.State>, zobrazí se kolem ostatních <xref:System.Activities.Statements.State>čtyři trojúhelníky. Pokud je <xref:System.Activities.Statements.State> přehozena na jeden ze čtyř trojúhelníků, přidá se do stavového počítače a ze zdrojového <xref:System.Activities.Statements.State> se vytvoří přechod na vyřazený cílový <xref:System.Activities.Statements.State>. Další informace najdete v tématu [přechod](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Vlastnosti aktivity stavu v Návrhář postupu provádění

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.State>, které lze nastavit pomocí návrháře pracovních postupů, a popisuje, jak se používají v návrháři. Některé z těchto vlastností lze upravit v mřížce vlastností a některé lze upravovat na návrhové ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Nepravda|Určuje popisný název návrháře <xref:System.Activities.Statements.State> aktivity v hlavičce. Výchozí hodnota je **State (stav**). Hodnotu lze upravit v mřížce vlastností nebo přímo v záhlaví návrháře aktivit. <xref:System.Activities.Statements.State.DisplayName%2A> se používá v navigaci s popisem cesty, které se zobrazí v horní části návrháře pracovních postupů.<br /><br /> I když <xref:System.Activities.Statements.State.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.State.Entry%2A>|Nepravda|Určuje akci, která nastane, když je tento stav převeden na. Pokud je aktivita <xref:System.Activities.Statements.State> rozbalena, lze tuto hodnotu nastavit přetažením aktivity z **panelu nástrojů** a jejím přetažením do oddílu **vstup** ve stavu.|
|<xref:System.Activities.Statements.State.Exit%2A>|Nepravda|Určuje akci, která nastane, když je tento stav přepnut z. Při rozbalení aktivity <xref:System.Activities.Statements.State> lze tuto hodnotu nastavit přetažením aktivity z **panelu nástrojů** a jejím přeřazením do **ukončovacího** oddílu daného stavu.|
|<xref:System.Activities.Statements.State.Transitions%2A>|Nepravda|Zobrazuje seznam možných přechodů pocházejících z <xref:System.Activities.Statements.State>. Každá položka v seznamu obsahuje odkaz na související <xref:System.Activities.Statements.Transition> a cílový <xref:System.Activities.Statements.State>. Po kliknutí na odkaz dojde k přepnutí návrháře na rozšířené zobrazení <xref:System.Activities.Statements.Transition> nebo <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>Viz také:

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)
