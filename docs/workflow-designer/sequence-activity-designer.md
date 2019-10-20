---
title: Návrhář aktivity Návrhář postupu provádění-Sequence
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 116e8c31a6d7cad2e5c6da95bc66e34a0d11163a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649952"
---
# <a name="sequence-activity-designer"></a>Návrhář aktivity Sequence

Aktivita <xref:System.Activities.Statements.Sequence> obsahuje uspořádanou kolekci podřízených aktivit, které se spustí v daném pořadí.

Dalším způsobem, jak spustit sadu aktivit v uvedeném pořadí, je použít aktivitu <xref:System.Activities.Statements.Flowchart>. Zvažte použití [vývojového diagramu](../workflow-designer/flowchart-activity-designer.md) v případě jednoduchého toku větvení nebo smyčky programu, který chcete modelovat diagrammatically.

## <a name="using-the-sequence-activity-designer"></a>Pomocí návrháře aktivity sekvence

Chcete-li přidat aktivitu <xref:System.Activities.Statements.Sequence>, přetáhněte návrháře aktivity **sekvence** z **panelu nástrojů** a přetáhněte jej na plochu Návrhář postupu provádění. Chcete-li do této aktivity <xref:System.Activities.Statements.Sequence> přidat podřízenou aktivitu, přetáhněte ji ze **sady nástrojů** a umístěte ji na trojúhelník v poli s textem nápovědy "Sem přetáhněte aktivitu".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Vlastnosti aktivity sekvence v Návrhář postupu provádění

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.Sequence> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje popisný název návrháře <xref:System.Activities.Statements.Sequence> aktivity v hlavičce. Výchozí hodnota je Sequence. Hodnotu lze upravit v mřížce vlastností nebo přímo v záhlaví návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|

## <a name="see-also"></a>Viz také:

- [Vývojový diagram](../workflow-designer/flowchart-activity-designer.md)
- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)