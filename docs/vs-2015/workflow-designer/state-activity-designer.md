---
title: Návrhář aktivity stavu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c1eea76a2593f4c0de817b8439361bd1be37b5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663200"
---
# <a name="state-activity-designer"></a>Návrhář aktivity State
<xref:System.Activities.Statements.State>Představuje stav, ve kterém může být Stavový počítač v.

## <a name="using-the-state-activity-designer"></a>Použití návrháře aktivity stavu
 Chcete-li přidat <xref:System.Activities.Statements.State> do pracovního postupu, přetáhněte návrháře aktivity **stavu** z části **Stavový počítač** v **sadě nástrojů** a umístěte jej na <xref:System.Activities.Statements.StateMachine> aktivitu na [!INCLUDE[wfd1](../includes/wfd1-md.md)] povrchu. <xref:System.Activities.Statements.State>Aktivitu lze vynechat na <xref:System.Activities.Statements.StateMachine> a přechody přidané později. Pokud <xref:System.Activities.Statements.State> je aktivita vyřazena, lze vytvořit přechod. Chcete-li přidat <xref:System.Activities.Statements.State> aktivitu a vytvořit přechod v jednom kroku, přetáhněte aktivitu **stavu** z části **Stavový počítač** v **sadě nástrojů** a umístěte ji do jiného stavu v Návrháři postupu. Když je přetažení <xref:System.Activities.Statements.State> nad jiným <xref:System.Activities.Statements.State> , zobrazí se kolem sebe čtyři trojúhelníky <xref:System.Activities.Statements.State> . Pokud <xref:System.Activities.Statements.State> je vyhozena na jeden ze čtyř trojúhelníků, je přidána do stavového počítače a přechod je vytvořen ze zdroje <xref:System.Activities.Statements.State> do vyřazeného cíle <xref:System.Activities.Statements.State> . Další informace najdete v tématu [přechod](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Vlastnosti aktivity stavu v Návrhář postupu provádění
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.State> vlastnosti, které lze nastavit pomocí návrháře pracovních postupů, a popisuje, jak se používají v návrháři. Některé z těchto vlastností lze upravit v mřížce vlastností a některé lze upravovat na návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Ne|Určuje popisný název <xref:System.Activities.Statements.State> návrháře aktivit v hlavičce. Výchozí hodnota je **State (stav**). Hodnotu lze upravit v mřížce vlastností nebo přímo v záhlaví návrháře aktivit. <xref:System.Activities.Statements.State.DisplayName%2A>Používá se v navigaci s popisem cesty, které se zobrazí v horní části návrháře pracovních postupů.<br /><br /> I když <xref:System.Activities.Statements.State.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.State.Entry%2A>|Ne|Určuje akci, která nastane, když je tento stav převeden na. Když <xref:System.Activities.Statements.State> se aktivita rozbalí, tato hodnota se dá nastavit tak, že ji přetáhnete ze **sady nástrojů** a přetáhnete ji do oddílu pro **zadávání** .|
|<xref:System.Activities.Statements.State.Exit%2A>|Ne|Určuje akci, která nastane, když je tento stav přepnut z. Když <xref:System.Activities.Statements.State> je aktivita rozbalená, tato hodnota se dá nastavit tak, že ji přetáhnete z **panelu nástrojů** a přetáhnete ji do **ukončovacího** oddílu daného stavu.|
|<xref:System.Activities.Statements.State.Transitions%2A>|Ne|Zobrazuje seznam možných přechodů pocházejících z <xref:System.Activities.Statements.State> . Každá položka v seznamu má odkaz na přidružený <xref:System.Activities.Statements.Transition> a cíl <xref:System.Activities.Statements.State> . Po kliknutí na odkaz dojde k přepnutí návrháře na rozšířené zobrazení <xref:System.Activities.Statements.Transition> nebo <xref:System.Activities.Statements.State> .|

## <a name="see-also"></a>Viz také
 [Přechod](../workflow-designer/transition-activity-designer.md) na [StateMachine](../workflow-designer/statemachine-activity-designer.md) [FinalState](../workflow-designer/finalstate-activity-designer.md)