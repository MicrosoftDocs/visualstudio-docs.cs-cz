---
title: Zrušit &lt; &gt; Návrháře aktivitycollection T | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657025"
---
# <a name="clearcollectionlttgt-activity-designer"></a>Zrušit &lt; &gt; Návrháře aktivitycollection T
Návrhář aktivity **ClearCollection \<T> ** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.ClearCollection%601> aktivity.

## <a name="the-clearcollectiont-activity"></a>Aktivita ClearCollection \<T>
 Tato <xref:System.Activities.Statements.ClearCollection%601> Aktivita vymaže zadanou kolekci všech položek.

### <a name="using-the-clearcollectiont-activity-designer"></a>Pomocí \<T> návrháře aktivit ClearCollection
 Návrhář ** \<T> aktivity ClearCollection** se dá najít v kategorii **kolekce** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář aktivity **ClearCollection \<T> ** lze přetáhnout ze **sady nástrojů** a umístit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.ClearCollection%601> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> ClearCollection \<Int32> . (Ve výchozím nastavení je *pro TypeArgument* typu **Int32**. To lze změnit v mřížce vlastností.) <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity **ClearCollection \<T> ** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti je nutné upravit v mřížce vlastností.

### <a name="the-clearcollectiont-properties"></a>Vlastnosti ClearCollection \<T>
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.ClearCollection%601> vlastnosti a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje nepovinný popisný název <xref:System.Activities.Statements.ClearCollection%601> aktivity. Výchozí hodnota je ClearCollection \<Int32> . I když není <xref:System.Activities.Activity.DisplayName%2A> hodnota striktně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Ano|Určuje kolekci, do které mají být položky vymazány. Tato kolekce je typu **ICollection \<TypeArgument> .** Chcete-li zadat kolekci, zadejte výraz Visual Basic v mřížce vlastností.|
|*Pro TypeArgument*|Ano|Určuje typ T položek obsažených v <xref:System.Collections.Generic.ICollection%601> . Ve výchozím nastavení je tento typ *pro TypeArgument* nastaven na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu *pro TypeArgument* v poli se seznamem v mřížce vlastností.|

## <a name="see-also"></a>Viz také
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) kolekce [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)