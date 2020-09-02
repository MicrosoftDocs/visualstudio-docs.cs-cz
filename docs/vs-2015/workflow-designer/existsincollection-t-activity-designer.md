---
title: '&lt; &gt; Návrhář aktivity ExistsInCollection T | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656737"
---
# <a name="existsincollectionlttgt-activity-designer"></a>&lt; &gt; Návrhář aktivity ExistsInCollection T
Návrhář **aktivity \<T> ExistsInCollection** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.ExistsInCollection%601> aktivity.

## <a name="the-existsincollectiont-activity"></a>Aktivita ExistsInCollection \<T>
 <xref:System.Activities.Statements.ExistsInCollection%601>Aktivita určuje, zda zadaná položka existuje v určité kolekci.

### <a name="using-the-existsincollectiont-activity-designer"></a>Pomocí \<T> Návrháře aktivity ExistsInCollection
 Návrhář **aktivity \<T> ExistsInCollection** se dá najít v kategorii **kolekce** sady **nástrojů**, ke které se dostanete kliknutím na kartu panelu **nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář **aktivity \<T> ExistsInCollection** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.ExistsInCollection%601> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection \<Int32> . (Ve výchozím nastavení je *pro TypeArgument* typu **Int32**. Dá se změnit v mřížce vlastností.)  <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity ** \<T> ExistsInCollection** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti je nutné upravit v mřížce vlastností.

### <a name="the-existsincollectiont-properties"></a>Vlastnosti ExistsInCollection \<T>
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.ExistsInCollection%601> vlastnosti a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.ExistsInCollection%601> aktivity Výchozí hodnota je ExistsInCollection \<Int32> . I když není <xref:System.Activities.Activity.DisplayName%2A> hodnota striktně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Ano|Položka, která se má přidat do \<T> kolekce Tato položka je typu *T* , která je typu *pro TypeArgument*. Chcete-li zadat položku, zadejte výraz Visual Basic v mřížce vlastností.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Ano|Kolekce, do které má být položka přidána. Tato kolekce je typu **ICollection \<TypeArgument> .** Chcete-li zadat kolekci, zadejte výraz Visual Basic v mřížce vlastností.|
|*Pro TypeArgument*|Ano|Typ T položek obsažených v <xref:System.Collections.Generic.ICollection%601> . Ve výchozím nastavení je tento typ *pro TypeArgument* nastaven na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu *pro TypeArgument* v poli se seznamem v mřížce vlastností.|
|<xref:System.Activities.Activity%601.Result%2A>|Ne|Hodnota, která označuje, zda zadaná položka v kolekci existuje. Chcete-li zadat proměnnou pro svázání s výsledkem, zadejte Visual Basic proměnnou v mřížce vlastností.|

## <a name="see-also"></a>Viz také
 [Kolekce](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)