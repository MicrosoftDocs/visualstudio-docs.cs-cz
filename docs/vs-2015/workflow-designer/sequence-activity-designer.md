---
title: Návrhář aktivity sekvence | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3acf02ab478eee244557e04f19f78ba2d5f0b950
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663264"
---
# <a name="sequence-activity-designer"></a>Návrhář aktivity Sequence
<xref:System.Activities.Statements.Sequence>Aktivita obsahuje uspořádanou kolekci podřízených aktivit, které se spustí v daném pořadí.

 Dalším způsobem, jak spustit sadu aktivit v daném pořadí, je použít <xref:System.Activities.Statements.Flowchart> aktivitu. Zvažte použití [vývojového diagramu](../workflow-designer/flowchart-activity-designer.md) v případě jednoduchého toku větvení nebo smyčky programu, který chcete modelovat diagrammatically.

## <a name="using-the-sequence-activity-designer"></a>Pomocí návrháře aktivity sekvence
 Chcete-li přidat <xref:System.Activities.Statements.Sequence> aktivitu, přetáhněte návrháře aktivity **sekvence** z **panelu nástrojů** a umístěte jej na [!INCLUDE[wfd1](../includes/wfd1-md.md)] plochu. Chcete-li do této aktivity přidat podřízenou aktivitu <xref:System.Activities.Statements.Sequence> , přetáhněte ji ze **sady nástrojů** a umístěte ji na trojúhelník v poli s textem nápovědy "Sem přetáhněte aktivitu".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Vlastnosti aktivity sekvence v Návrhář postupu provádění
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Sequence> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje popisný název <xref:System.Activities.Statements.Sequence> návrháře aktivit v hlavičce. Výchozí hodnota je Sequence. Hodnotu lze upravit v mřížce vlastností nebo přímo v záhlaví návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|

## <a name="see-also"></a>Viz také
 [Tok ovládacího prvku](../workflow-designer/control-flow-activity-designers.md) [vývojového diagramu](../workflow-designer/flowchart-activity-designer.md)