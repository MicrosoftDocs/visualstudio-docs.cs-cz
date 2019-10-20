---
title: Návrhář aktivity Návrhář postupu provádění-ForEach &lt;T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faf2f62c482deac963f597c9861fbf2acedc945c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650387"
---
# <a name="foreachlttgt-activity-designer"></a>Návrhář aktivity &gt; &lt;T ForEach

Aktivita <xref:System.Activities.Statements.ForEach%601> spustí aktivitu obsaženou v <xref:System.Activities.Statements.ForEach%601.Body%2A> pro každou položku v zadané kolekci <xref:System.Activities.Statements.ForEach%601.Values%2A>.

## <a name="foreacht-properties-in-the-workflow-designer"></a>@No__t_0 vlastnosti ForEach < T v Návrhář postupu provádění

Následující tabulka uvádí nejužitečnější vlastnosti <xref:System.Activities.Statements.ForEach%601> aktivity a popisuje jejich použití v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.ForEach%601>. Výchozí hodnota je ForEach < Int32 \>. I když hodnota <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Podmínka|Kolekce položek, které se mají iterovat Chcete-li nastavit <xref:System.Activities.Statements.ForEach%601.Values%2A>, zadejte výraz Visual Basic do pole **hodnoty** v Návrháři **< v foreach \>** nebo v mřížce vlastností.|
|*Pro TypeArgument*|Podmínka|Typ položek v kolekci <xref:System.Activities.Statements.ForEach%601.Values%2A> určených obecným parametrem *t*. Ve výchozím nastavení je *pro TypeArgument* nastaveno na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu pole se seznamem *pro TypeArgument* v mřížce vlastností.|

Ve výchozím nastavení je iterátor smyčky pojmenovaný **Item**. V Návrháři aktivity <xref:System.Activities.Statements.ForEach%601> můžete změnit název proměnné iterátoru. Iterátor smyčky lze použít ve výrazech podřízených objektů aktivity <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>Viz také:

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)