---
title: Návrhář aktivity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b35fe7f1b55dde25ec896f230f66cef00d24eed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659061"
---
# <a name="if-activity-designer"></a>Návrhář aktivity If
<xref:System.Activities.Statements.If>Aktivita vyhodnocuje podmínku a provede aktivitu v závislosti na výsledcích tohoto vyhodnocení. Tato aktivita je nejužitečnější při použití stylu procedurálního modelování programování. <xref:System.Activities.Statements.If>Aktivita může být vnořena v rámci <xref:System.Activities.Statements.Sequence> aktivity nebo <xref:System.Activities.Statements.Parallel> aktivity, například. Pokud používáte <xref:System.Activities.Statements.Flowchart> aktivitu, zvažte <xref:System.Activities.Statements.FlowDecision> místo toho použití aktivity.

## <a name="if-properties-in-the-workflow-designer"></a>Pokud se v Návrhář postupu provádění vlastnosti
 Následující tabulka uvádí nejužitečnější <xref:System.Activities.Statements.If> vlastnosti aktivity a popisuje jejich použití v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.If.Condition%2A>|Ano|Podmínka, která určuje, která podřízená aktivita má být provedena. Chcete-li nastavit <xref:System.Activities.Statements.If.Condition%2A> , zadejte [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] výraz do pole **Podmínka** v Návrháři aktivity **if** nebo v mřížce vlastností.|
|<xref:System.Activities.Statements.If.Else%2A>|Ne|Aktivita, která se má provést, pokud <xref:System.Activities.Statements.If.Condition%2A> je **hodnota false** Chcete-li přidat aktivitu, která je spuštěna <xref:System.Activities.Statements.If.Else%2A> větví, přetáhněte aktivitu ze **sady nástrojů** do pole **Else** v Návrháři aktivity **if** s textem nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.If.Then%2A>|Ne|Aktivita, která se má provést, pokud <xref:System.Activities.Statements.If.Condition%2A> je **hodnota true**. Chcete-li přidat aktivitu, která je spouštěna <xref:System.Activities.Statements.If.Then%2A> větví, přetáhněte aktivitu ze **sady nástrojů** do pole **Then** , které se nachází **If** v Návrháři aktivity, pomocí textu nápovědy "Sem přetáhněte aktivitu".|

## <a name="see-also"></a>Viz také
 [Sekvence](../workflow-designer/sequence-activity-designer.md) [paralelního](../workflow-designer/parallel-activity-designer.md) [řízení toku](../workflow-designer/control-flow-activity-designers.md)