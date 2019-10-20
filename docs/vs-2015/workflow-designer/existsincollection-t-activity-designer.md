---
title: Návrhář aktivit &gt; ExistsInCollection &lt;T | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 08aabbcb7dbef2df9a3affa8589a9c6d4205ac58
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656737"
---
# <a name="existsincollectionlttgt-activity-designer"></a>Návrhář aktivity &gt; ExistsInCollection &lt;T
Návrhář aktivity **\<T > ExistsInCollection** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.ExistsInCollection%601>.

## <a name="the-existsincollectiont-activity"></a>Aktivita > ExistsInCollection \<T
 Aktivita <xref:System.Activities.Statements.ExistsInCollection%601> určuje, zda zadaná položka existuje v určité kolekci.

### <a name="using-the-existsincollectiont-activity-designer"></a>Použití návrháře aktivit > ExistsInCollection \<T
 Návrhář aktivity **ExistsInCollection \<T >** můžete najít v kategorii **kolekce** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** z **Zobrazit** nabídku nebo CTRL + ALT + X.)

 Návrhář aktivity **ExistsInCollection \<T >** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.ExistsInCollection%601> s výchozím <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection \<Int32 >. (Ve výchozím nastavení je *pro TypeArgument* typu **Int32**. Dá se změnit v mřížce vlastností.)  Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v hlavičce návrháře aktivity **> \<T ExistsInCollection** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti je nutné upravit v mřížce vlastností.

### <a name="the-existsincollectiont-properties"></a>Vlastnosti ExistsInCollection \<T >
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.ExistsInCollection%601> a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.ExistsInCollection%601>. Výchozí hodnota je ExistsInCollection \<Int32 >. I když hodnota <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Podmínka|Položka, kterou chcete přidat do kolekce \<T >. Tato položka je typu *T* , která je typu *pro TypeArgument*. Chcete-li zadat položku, zadejte výraz Visual Basic v mřížce vlastností.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Podmínka|Kolekce, do které má být položka přidána. Tato kolekce je typu **ICollection \<TypeArgument >.** Chcete-li zadat kolekci, zadejte výraz Visual Basic v mřížce vlastností.|
|*Pro TypeArgument*|Podmínka|Typ T položek obsažených v <xref:System.Collections.Generic.ICollection%601>. Ve výchozím nastavení je tento typ *pro TypeArgument* nastaven na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu *pro TypeArgument* v poli se seznamem v mřížce vlastností.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Hodnota, která označuje, zda zadaná položka v kolekci existuje. Chcete-li zadat proměnnou pro svázání s výsledkem, zadejte Visual Basic proměnnou v mřížce vlastností.|

## <a name="see-also"></a>Viz také
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [clearcollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) [RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)