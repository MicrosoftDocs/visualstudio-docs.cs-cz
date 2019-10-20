---
title: Návrhář &lt;T &gt; aktivity ForEach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d41451ada0e37f953e9d611a4e3733815a9d347b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656658"
---
# <a name="foreachlttgt-activity-designer"></a>Návrhář aktivity &gt; &lt;T ForEach
Aktivita <xref:System.Activities.Statements.ForEach%601> spustí aktivitu obsaženou v <xref:System.Activities.Statements.ForEach%601.Body%2A> pro každou položku v zadané kolekci <xref:System.Activities.Statements.ForEach%601.Values%2A>.

## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach \<T > vlastnosti v Návrhář postupu provádění
 Následující tabulka uvádí nejužitečnější vlastnosti <xref:System.Activities.Statements.ForEach%601> aktivity a popisuje jejich použití v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.ForEach%601>. Výchozí hodnota je ForEach \<Int32 >. I když hodnota <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Podmínka|Kolekce položek, které se mají iterovat Chcete-li nastavit <xref:System.Activities.Statements.ForEach%601.Values%2A>, zadejte výraz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] do pole **hodnoty** v nabídce **foreach \<T >** návrháře aktivity nebo v mřížce vlastností.|
|*Pro TypeArgument*|Podmínka|Typ položek v kolekci <xref:System.Activities.Statements.ForEach%601.Values%2A> určených obecným parametrem *t*. Ve výchozím nastavení je *pro TypeArgument* nastaveno na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu pole se seznamem *pro TypeArgument* v mřížce vlastností.|

 Ve výchozím nastavení je iterátor smyčky pojmenovaný **Item**. V Návrháři aktivity <xref:System.Activities.Statements.ForEach%601> můžete změnit název proměnné iterátoru. Iterátor smyčky lze použít ve výrazech podřízených objektů aktivity <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>Viz také
 [Tok řízení](../workflow-designer/control-flow-activity-designers.md) [> ParallelForEach \<T](../workflow-designer/parallelforeach-t-activity-designer.md)