---
title: Návrhář postupu provádění – Pokud návrháře aktivit
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 716f2b13758864d5eda449967990f9e5be399a9d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822837"
---
# <a name="if-activity-designer"></a>Návrhář aktivity If

<xref:System.Activities.Statements.If> Aktivity vyhodnocuje podmínku a provede aktivitu v závislosti na výsledcích hodnocení. Tato aktivita je nejužitečnější při použití procedurální modelování styl programování. <xref:System.Activities.Statements.If> Aktivity mohou být vnořené uvnitř <xref:System.Activities.Statements.Sequence> aktivity nebo <xref:System.Activities.Statements.Parallel> aktivity, například. Pokud používáte <xref:System.Activities.Statements.Flowchart> aktivity, zvažte použití <xref:System.Activities.Statements.FlowDecision> aktivity místo.

## <a name="if-properties-in-the-workflow-designer"></a>Pokud vlastnosti v Návrháři postupu provádění

V následující tabulce jsou uvedeny nejužitečnější <xref:System.Activities.Statements.If> vlastnosti aktivit a popisuje, jak je používat v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Hodnota TRUE|Podmínka, která určuje, které podřízené aktivity ke spuštění. Chcete-li nastavit <xref:System.Activities.Statements.If.Condition%2A>, zadejte výraz jazyka Visual Basic v **podmínku** pole na **Pokud** aktivity návrháře nebo v mřížce vlastností.|
|<xref:System.Activities.Statements.If.Else%2A>|False|Aktivita spustit, když <xref:System.Activities.Statements.If.Condition%2A> je **false**. Přidat aktivitu, která provádí <xref:System.Activities.Statements.If.Else%2A> větev, přetáhněte aktivitu z **nástrojů** do **Else** pole na **Pokud** Návrhář aktivity s text nápovědy " Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.If.Then%2A>|False|Aktivita spustit, když <xref:System.Activities.Statements.If.Condition%2A> je **true**. Přidat aktivitu, která provádí <xref:System.Activities.Statements.If.Then%2A> větev, přetáhněte aktivitu z **nástrojů** do **pak** pole na **Pokud** Návrhář aktivity s text nápovědy " Sem přetáhněte aktivitu".|

## <a name="see-also"></a>Viz také:

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)