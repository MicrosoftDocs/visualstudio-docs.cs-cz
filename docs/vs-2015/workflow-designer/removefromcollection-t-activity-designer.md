---
title: Návrhář aktivit &gt; RemoveFromCollection &lt;T | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ac088c6e5710fcd1b7c401402ad473488f89524
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672566"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>Návrhář aktivity &gt; RemoveFromCollection &lt;T
Návrhář aktivity **\<T > RemoveFromCollection** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.RemoveFromCollection%601>.

## <a name="the-removefromcollectiont-activity"></a>Aktivita > RemoveFromCollection \<T
 Aktivita <xref:System.Activities.Statements.RemoveFromCollection%601> odstraní zadanou položku z konkrétní kolekce.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Použití návrháře aktivit > RemoveFromCollection \<T
 Návrhář aktivity **RemoveFromCollection \<T >** můžete najít v kategorii **kolekce** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** z v nabídce **zobrazení** nebo v kombinaci kláves CTRL + ALT + X.)

 Návrhář aktivity **RemoveFromCollection \<T >** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.RemoveFromCollection%601> s výchozím <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection \<Int32 >. Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v hlavičce návrháře aktivity **> \<T RemoveFromCollection** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti je nutné upravit v mřížce vlastností.

### <a name="the-removefromcollectiont-properties"></a>Vlastnosti RemoveFromCollection \<T >
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.RemoveFromCollection%601> a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Volitelný popisný název aktivity <xref:System.Activities.Statements.RemoveFromCollection%601>. Výchozím nastavením je RemoveFromCollection \<Int32 >.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Podmínka|Položka, kterou chcete přidat do **kolekce \<T >** . Tato položka je typu *T*, který je typu *pro TypeArgument*. Chcete-li zadat položku, zadejte výraz Visual Basic v mřížce vlastností.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Podmínka|Kolekce, do které má být položka přidána. Tato kolekce je typu **ICollection \<TypeArgument >.** Chcete-li zadat kolekci, zadejte výraz Visual Basic v mřížce vlastností.|
|*Pro TypeArgument*|Podmínka|Typ T položek obsažených v <xref:System.Collections.Generic.ICollection%601>. Ve výchozím nastavení je tento typ *pro TypeArgument* nastaven na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu *pro TypeArgument* v poli se seznamem v mřížce vlastností.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Hodnota, která označuje, zda byla zadaná položka odebrána z kolekce. Chcete-li zadat proměnnou pro svázání s výsledkem, zadejte proměnnou v mřížce vlastností.|

## <a name="see-also"></a>Viz také
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [clearcollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md)