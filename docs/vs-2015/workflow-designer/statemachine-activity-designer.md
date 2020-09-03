---
title: Návrhář aktivity StateMachine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fc9d34e06ca443b39a1a57aa88fee1155f47a8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660108"
---
# <a name="statemachine-activity-designer"></a>Návrhář aktivity StateMachine
<xref:System.Activities.Statements.StateMachine>Aktivita obsahuje kolekci stavů a pracovních postupů modelů, které používají známé stavové paradigma počítače.

## <a name="using-the-statemachine-activity-designer"></a>Použití návrháře aktivit StateMachine
 Chcete-li přidat <xref:System.Activities.Statements.StateMachine> aktivitu, přetáhněte návrháře aktivity **StateMachine** z části **Stavový počítač** v **panelu nástrojů** a přetáhněte jej na [!INCLUDE[wfd1](../includes/wfd1-md.md)] plochu. Chcete-li do této aktivity přidat podřízený stav <xref:System.Activities.Statements.StateMachine> , přetáhněte <xref:System.Activities.Statements.State> <xref:System.Activities.Core.Presentation.FinalState> ji ze **sady nástrojů** a umístěte ji do stavového **stroje**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Vlastnosti aktivity StateMachine v Návrhář postupu provádění
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.StateMachine> vlastnosti, které lze nastavit pomocí návrháře pracovních postupů, a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé lze upravovat na návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje popisný název <xref:System.Activities.Statements.StateMachine> návrháře aktivit v hlavičce. Výchozí hodnota je **StateMachine**. Hodnotu lze upravit v mřížce vlastností nebo přímo v záhlaví návrháře aktivit. <xref:System.Activities.Activity.DisplayName%2A>Používá se v navigaci s popisem cesty, které se zobrazí v horní části návrháře pracovních postupů.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|

## <a name="see-also"></a>Viz také
 [Tok ovládacího prvku](../workflow-designer/control-flow-activity-designers.md) [vývojového diagramu](../workflow-designer/flowchart-activity-designer.md)