---
title: '&lt; &gt; Návrhář aktivity AddToCollection T | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50deab447b3dcb93d352e73fc4765d913b4d24bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659197"
---
# <a name="addtocollectionlttgt-activity-designer"></a>&lt; &gt; Návrhář aktivity AddToCollection T
Návrhář **aktivity \<T> AddToCollection** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.AddToCollection%601> aktivity.

## <a name="the-addtocollectiont-activity"></a>Aktivita AddToCollection \<T>
 <xref:System.Activities.Statements.AddToCollection%601>Aktivita přidá položku do kolekce.

### <a name="using-the-addtocollectiont-activity-designer"></a>Pomocí \<T> Návrháře aktivity AddToCollection
 Návrhář **aktivity \<T> AddToCollection** se dá najít v kategorii **kolekce** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář **aktivity \<T> AddToCollection** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.AddToCollection%601> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> AddToCollection \<Int32> . (Ve výchozím nastavení je *pro TypeArgument* typu **Int32**. To lze změnit v mřížce vlastností.) <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity ** \<T> AddToCollection** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti je nutné upravit v mřížce vlastností.

### <a name="the-addtocollectiont-properties"></a>Vlastnosti AddToCollection \<T>
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.AddToCollection%601> vlastnosti a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.AddToCollection%601> aktivity Výchozí hodnota je AddToCollection \<Int32> . I když není <xref:System.Activities.Activity.DisplayName%2A> hodnota striktně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Ano|Položka, která se má přidat do \<T> kolekce Tato položka je typu *T*, který je typu *pro TypeArgument*. Chcete-li zadat položku, zadejte výraz Visual Basic v mřížce vlastností.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Ano|Kolekce, do které má být položka přidána. Tato kolekce je typu **ICollection \<TypeArgument> **. Chcete-li zadat kolekci, zadejte výraz Visual Basic v mřížce vlastností.|
|*Pro TypeArgument*|Ano|Typ T položek obsažených v <xref:System.Collections.Generic.ICollection%601> . Ve výchozím nastavení je tento typ *pro TypeArgument* nastaven na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu *pro TypeArgument* v poli se seznamem v mřížce vlastností.|

## <a name="see-also"></a>Viz také
 [AddToCollection kolekce](../workflow-designer/collection-activity-designers.md) [– \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md) [ \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) [Návrhář aktivity ClearCollection ExistsInCollection RemoveFromCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md)