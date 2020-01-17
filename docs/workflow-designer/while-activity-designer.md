---
title: Návrhář postupu provádění – Návrhář aktivity
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77954925533c51885a056f7156121e68851ad769
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115165"
---
# <a name="while-activity-designer"></a>Návrhář aktivity While

Aktivita <xref:System.Activities.Statements.While> spustí aktivitu obsaženou v <xref:System.Activities.Statements.While.Body%2A>, zatímco zadané <xref:System.Activities.Statements.While.Condition%2A> vyhodnotí jako **true**. Obsažená aktivita nemusí být nikdy spuštěna. Pokud chcete, aby byla obsažená aktivita provedena aspoň jednou, použijte místo toho <xref:System.Activities.Statements.DoWhile> aktivitu.

## <a name="while-properties-in-workflow-designer"></a>Vlastnosti v Návrhář postupu provádění

Následující tabulka uvádí nejužitečnější vlastnosti <xref:System.Activities.Statements.While> aktivity a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Určuje popisný název návrháře <xref:System.Activities.Statements.While> aktivity v hlavičce. Výchozí hodnota je while. Hodnotu lze upravit v okně **vlastnosti** nebo přímo v hlavičce návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.While.Body%2A>|Nepravda|Obsahuje aktivitu, která se má provést, když se <xref:System.Activities.Statements.While.Condition%2A> vyhodnotí jako **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Pravda|Obsahuje výraz Visual Basic, který je vyhodnocován pro určení, zda má být provedena aktivita v <xref:System.Activities.Statements.While.Body%2A>.|

## <a name="see-also"></a>Viz také:

- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
