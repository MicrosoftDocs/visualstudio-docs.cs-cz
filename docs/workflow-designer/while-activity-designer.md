---
title: Návrhář postupu provádění – Návrhář aktivity
description: Zjistěte, jak aktivita while spustí aktivitu obsaženou v těle, zatímco zadaná podmínka je vyhodnocena jako true.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9447d32f17283e7123e2f99490acc49c1613360d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837993"
---
# <a name="while-activity-designer"></a>Návrhář aktivity While

<xref:System.Activities.Statements.While>Aktivita spustí aktivitu obsaženou v době, <xref:System.Activities.Statements.While.Body%2A> kdy se určená hodnota <xref:System.Activities.Statements.While.Condition%2A> vyhodnotí jako **true**. Obsažená aktivita nemusí být nikdy spuštěna. Pokud chcete, aby byla obsažená aktivita provedena aspoň jednou, použijte <xref:System.Activities.Statements.DoWhile> místo ní aktivitu.

## <a name="while-properties-in-workflow-designer"></a>Vlastnosti v Návrhář postupu provádění

Následující tabulka uvádí nejužitečnější <xref:System.Activities.Statements.While> vlastnosti aktivity a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje popisný název <xref:System.Activities.Statements.While> návrháře aktivit v hlavičce. Výchozí hodnota je while. Hodnotu lze upravit v okně **vlastnosti** nebo přímo v hlavičce návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.While.Body%2A>|Ne|Obsahuje aktivitu, která se má provést, když se <xref:System.Activities.Statements.While.Condition%2A> vyhodnotí jako **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Ano|Obsahuje výraz Visual Basic, který je vyhodnocován pro určení, zda má být provedena aktivita v rámci <xref:System.Activities.Statements.While.Body%2A> .|

## <a name="see-also"></a>Viz také

- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
