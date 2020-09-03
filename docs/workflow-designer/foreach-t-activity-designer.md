---
title: Návrhář aktivity Návrhář postupu provádění – ForEach &lt; T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30d43351211a6ff857630b47f05be77e27bd7951
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593912"
---
# <a name="foreachlttgt-activity-designer"></a>&lt; &gt; Návrhář aktivity ForEach T

<xref:System.Activities.Statements.ForEach%601>Aktivita spustí aktivitu obsaženou ve svém <xref:System.Activities.Statements.ForEach%601.Body%2A> pro každou položku v zadané <xref:System.Activities.Statements.ForEach%601.Values%2A> kolekci.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Vlastnosti ForEach<T \> v Návrhář postupu provádění

Následující tabulka uvádí nejužitečnější <xref:System.Activities.Statements.ForEach%601> vlastnosti aktivity a popisuje jejich použití v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.ForEach%601> aktivity Výchozí hodnota je ForEach<Int32 \> . I když není <xref:System.Activities.Activity.DisplayName%2A> hodnota striktně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Ano|Kolekce položek, které se mají iterovat Chcete-li nastavit <xref:System.Activities.Statements.ForEach%601.Values%2A> , zadejte výraz Visual Basic do pole **hodnoty** v návrháři aktivity **foreach<T \> ** nebo v mřížce vlastností.|
|*Pro TypeArgument*|Ano|Typ položek v <xref:System.Activities.Statements.ForEach%601.Values%2A> kolekci určené obecným parametrem *T*. Ve výchozím nastavení je *pro TypeArgument* nastaveno na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu pole se seznamem *pro TypeArgument* v mřížce vlastností.|

Ve výchozím nastavení je iterátor smyčky pojmenovaný **Item**. V Návrháři aktivit můžete změnit název proměnné iterátoru <xref:System.Activities.Statements.ForEach%601> . Iterátor smyčky lze použít ve výrazech v podřízených objektech <xref:System.Activities.Statements.ForEach%601> aktivity.

## <a name="see-also"></a>Viz také

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
