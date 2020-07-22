---
title: Návrhář aktivity Návrhář postupu provádění-Sequence
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77980077a580724f6db6bb5a544200890421d8e5
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875966"
---
# <a name="sequence-activity-designer"></a>Návrhář aktivity Sequence

<xref:System.Activities.Statements.Sequence>Aktivita obsahuje uspořádanou kolekci podřízených aktivit, které se spustí v daném pořadí.

Dalším způsobem, jak spustit sadu aktivit v daném pořadí, je použít <xref:System.Activities.Statements.Flowchart> aktivitu. Zvažte použití [vývojového diagramu](../workflow-designer/flowchart-activity-designer.md) v případě jednoduchého toku větvení nebo smyčky programu, který chcete modelovat diagrammatically.

## <a name="using-the-sequence-activity-designer"></a>Pomocí návrháře aktivity sekvence

Chcete-li přidat <xref:System.Activities.Statements.Sequence> aktivitu, přetáhněte návrháře aktivity **sekvence** z **panelu nástrojů** a umístěte jej na Návrhář postupu provádění plochu. Chcete-li do této aktivity přidat podřízenou aktivitu <xref:System.Activities.Statements.Sequence> , přetáhněte ji ze **sady nástrojů** a umístěte ji na trojúhelník v poli s textem nápovědy "Sem přetáhněte aktivitu".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Vlastnosti aktivity sekvence v Návrhář postupu provádění

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Sequence> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Určuje popisný název <xref:System.Activities.Statements.Sequence> návrháře aktivit v hlavičce. Výchozí hodnota je Sequence. Hodnotu lze upravit v mřížce vlastností nebo přímo v záhlaví návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|

## <a name="see-also"></a>Viz také

- [Vývojový diagram](../workflow-designer/flowchart-activity-designer.md)
- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)