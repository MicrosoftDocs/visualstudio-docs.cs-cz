---
title: '&lt; &gt; Návrhář aktivity RemoveFromCollection T | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672566"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>&lt; &gt; Návrhář aktivity RemoveFromCollection T
Návrhář **aktivity \<T> RemoveFromCollection** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.RemoveFromCollection%601> aktivity.

## <a name="the-removefromcollectiont-activity"></a>Aktivita RemoveFromCollection \<T>
 <xref:System.Activities.Statements.RemoveFromCollection%601>Aktivita Odebere zadanou položku z konkrétní kolekce.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Pomocí \<T> Návrháře aktivity RemoveFromCollection
 Návrhář **aktivity \<T> RemoveFromCollection** se dá najít v kategorii **kolekce** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panel nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář **aktivity \<T> RemoveFromCollection** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.RemoveFromCollection%601> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection \<Int32> . <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity ** \<T> RemoveFromCollection** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti je nutné upravit v mřížce vlastností.

### <a name="the-removefromcollectiont-properties"></a>Vlastnosti RemoveFromCollection \<T>
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.RemoveFromCollection%601> vlastnosti a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Volitelný popisný název <xref:System.Activities.Statements.RemoveFromCollection%601> aktivity. Výchozí hodnota je RemoveFromCollection \<Int32> .<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Ano|Položka, která se má přidat **do \<T> kolekce** Tato položka je typu *T*, který je typu *pro TypeArgument*. Chcete-li zadat položku, zadejte výraz Visual Basic v mřížce vlastností.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Ano|Kolekce, do které má být položka přidána. Tato kolekce je typu **ICollection \<TypeArgument> .** Chcete-li zadat kolekci, zadejte výraz Visual Basic v mřížce vlastností.|
|*Pro TypeArgument*|Ano|Typ T položek obsažených v <xref:System.Collections.Generic.ICollection%601> . Ve výchozím nastavení je tento typ *pro TypeArgument* nastaven na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu *pro TypeArgument* v poli se seznamem v mřížce vlastností.|
|<xref:System.Activities.Activity%601.Result%2A>|Ne|Hodnota, která označuje, zda byla zadaná položka odebrána z kolekce. Chcete-li zadat proměnnou pro svázání s výsledkem, zadejte proměnnou v mřížce vlastností.|

## <a name="see-also"></a>Viz také
 [Kolekce](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md)