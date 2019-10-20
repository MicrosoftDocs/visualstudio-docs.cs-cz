---
title: Návrhář postupu provádění – Návrhář aktivity
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6570a80de5be17b2893fc4105f057e655e841881
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649768"
---
# <a name="while-activity-designer"></a>Návrhář aktivity While

Aktivita <xref:System.Activities.Statements.While> spustí aktivitu obsaženou v <xref:System.Activities.Statements.While.Body%2A>, zatímco zadané <xref:System.Activities.Statements.While.Condition%2A> vyhodnotí jako **true**. Obsažená aktivita nemusí být nikdy spuštěna. Pokud chcete, aby byla obsažená aktivita provedena aspoň jednou, použijte místo toho <xref:System.Activities.Statements.DoWhile> aktivitu.

## <a name="while-properties-in-workflow-designer"></a>Vlastnosti v Návrhář postupu provádění

Následující tabulka uvádí nejužitečnější vlastnosti <xref:System.Activities.Statements.While> aktivity a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje popisný název návrháře <xref:System.Activities.Statements.While> aktivity v hlavičce. Výchozí hodnota je while. Hodnotu lze upravit v okně **vlastnosti** nebo přímo v hlavičce návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Obsahuje aktivitu, která se má provést, když se <xref:System.Activities.Statements.While.Condition%2A> vyhodnotí jako **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Podmínka|Obsahuje výraz Visual Basic, který je vyhodnocován pro určení, zda má být provedena aktivita v <xref:System.Activities.Statements.While.Body%2A>.|

## <a name="see-also"></a>Viz také:

- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)