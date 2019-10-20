---
title: Vymazatcollection &lt;T &gt; návrháře aktivit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2f1e0264d39c65601a70e8c24b51c7eceadf4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657025"
---
# <a name="clearcollectionlttgt-activity-designer"></a>Vymazatcollection &lt;T &gt; návrháře aktivit
Návrhář aktivity **clearcollection \<T >** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.ClearCollection%601>.

## <a name="the-clearcollectiont-activity"></a>Aktivita ClearCollection \<T >
 Aktivita <xref:System.Activities.Statements.ClearCollection%601> vymaže zadanou kolekci všech položek.

### <a name="using-the-clearcollectiont-activity-designer"></a>Použití návrháře \<T > aktivity ClearCollection
 Návrhář aktivity **clearcollection \<T >** lze najít v kategorii **kolekce** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** z **Zobrazit** nabídku nebo CTRL + ALT + X.)

 Návrhář aktivity **clearcollection \<T >** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.ClearCollection%601> s výchozí <xref:System.Activities.Activity.DisplayName%2A>ou ClearCollection \<Int32 >. (Ve výchozím nastavení je *pro TypeArgument* typu **Int32**. To lze změnit v mřížce vlastností.) Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v hlavičce návrháře aktivity **clearcollection \<T >** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti je nutné upravit v mřížce vlastností.

### <a name="the-clearcollectiont-properties"></a>Vlastnosti ClearCollection \<T >
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.ClearCollection%601> a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje nepovinný popisný název aktivity <xref:System.Activities.Statements.ClearCollection%601>. Výchozí hodnota je ClearCollection \<Int32 >. I když hodnota <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Podmínka|Určuje kolekci, do které mají být položky vymazány. Tato kolekce je typu **ICollection \<TypeArgument >.** Chcete-li zadat kolekci, zadejte výraz Visual Basic v mřížce vlastností.|
|*Pro TypeArgument*|Podmínka|Určuje typ T položek obsažených v <xref:System.Collections.Generic.ICollection%601>. Ve výchozím nastavení je tento typ *pro TypeArgument* nastaven na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu *pro TypeArgument* v poli se seznamem v mřížce vlastností.|

## <a name="see-also"></a>Viz také
 [Kolekce](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [ExistsInCollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)