---
title: Návrhář aktivity Návrhář postupu provádění – if
description: Zjistěte, jak aktivita if vyhodnocuje podmínku a spustí aktivitu v závislosti na výsledcích tohoto vyhodnocení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93f36a3c2b587718fe6889688baa50224f663c1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881357"
---
# <a name="if-activity-designer"></a>Návrhář aktivity If

<xref:System.Activities.Statements.If>Aktivita vyhodnocuje podmínku a provede aktivitu v závislosti na výsledcích tohoto vyhodnocení. Tato aktivita je nejužitečnější při použití stylu procedurálního modelování programování. <xref:System.Activities.Statements.If>Aktivita může být vnořena v rámci <xref:System.Activities.Statements.Sequence> aktivity nebo <xref:System.Activities.Statements.Parallel> aktivity, například. Pokud používáte <xref:System.Activities.Statements.Flowchart> aktivitu, zvažte <xref:System.Activities.Statements.FlowDecision> místo toho použití aktivity.

## <a name="if-properties-in-the-workflow-designer"></a>Pokud se v Návrhář postupu provádění vlastnosti

Následující tabulka uvádí nejužitečnější <xref:System.Activities.Statements.If> vlastnosti aktivity a popisuje jejich použití v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Ano|Podmínka, která určuje, která podřízená aktivita má být provedena. Chcete-li nastavit <xref:System.Activities.Statements.If.Condition%2A> , zadejte výraz Visual Basic do pole **Podmínka** v Návrháři aktivity **if** nebo v mřížce vlastností.|
|<xref:System.Activities.Statements.If.Else%2A>|Ne|Aktivita, která se má provést, pokud <xref:System.Activities.Statements.If.Condition%2A> je **hodnota false** Chcete-li přidat aktivitu, která je spuštěna <xref:System.Activities.Statements.If.Else%2A> větví, přetáhněte aktivitu ze **sady nástrojů** do pole **Else** v Návrháři aktivity **if** s textem nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.If.Then%2A>|Ne|Aktivita, která se má provést, pokud <xref:System.Activities.Statements.If.Condition%2A> je **hodnota true**. Chcete-li přidat aktivitu, která je spouštěna <xref:System.Activities.Statements.If.Then%2A> větví, přetáhněte aktivitu ze **sady nástrojů** do pole  , které se nachází  v Návrháři aktivity, pomocí textu nápovědy "Sem přetáhněte aktivitu".|

## <a name="see-also"></a>Viz také

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Zpracování](../workflow-designer/parallel-activity-designer.md)
- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
