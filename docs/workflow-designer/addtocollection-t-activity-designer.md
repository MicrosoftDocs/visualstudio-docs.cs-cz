---
title: Návrhář aktivity Návrhář postupu provádění – AddToCollection &lt; T &gt;
description: Přečtěte si, jak se <T> používá Návrhář aktivity AddToCollection k vytvoření a konfiguraci <T> aktivity AddToCollection.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a325cfa0ba00e798b3c663aac863737ba9aceb1f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438255"
---
# <a name="addtocollectiont-activity-designer"></a>Návrhář aktivity AddToCollection\<T>

Návrhář **aktivity \<T> AddToCollection** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.AddToCollection%601> aktivity.

## <a name="the-addtocollectiont-activity"></a>Aktivita AddToCollection \<T>

<xref:System.Activities.Statements.AddToCollection%601>Aktivita přidá položku do kolekce.

### <a name="using-the-addtocollectiont-activity-designer"></a>Pomocí \<T> Návrháře aktivity AddToCollection

Návrhář **aktivity \<T> AddToCollection** lze najít v kategorii **kolekce** sady **nástrojů** , ke které se dostanete kliknutím na kartu **panelu nástrojů** Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** + **+** + **X**.

Návrhář **aktivity \<T> AddToCollection** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Vyřazením návrháře aktivit **AddToCollection \<T>** <xref:System.Activities.Statements.AddToCollection%601> se vytvoří aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> AddToCollection<Int32 \> . (Ve výchozím nastavení je *pro TypeArgument* typu **Int32**. Pro TypeArgument lze změnit v mřížce vlastností.) <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity **AddToCollection<T \>** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti je nutné upravit v mřížce vlastností.

### <a name="the-addtocollectiont-properties"></a>Vlastnosti AddToCollection \<T>

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.AddToCollection%601> vlastnosti a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Popisný název <xref:System.Activities.Statements.AddToCollection%601> aktivity Výchozí hodnota je AddToCollection<Int32 \> . I když není <xref:System.Activities.Activity.DisplayName%2A> hodnota striktně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Pravda|Položka, která se má přidat do \<T> kolekce Tato položka je typu *T* , který je typu *pro TypeArgument*. Chcete-li zadat položku, zadejte výraz Visual Basic v mřížce vlastností.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Pravda|Kolekce, do které má být položka přidána. Tato kolekce je typu **ICollection<pro TypeArgument \>**. Chcete-li zadat kolekci, zadejte výraz Visual Basic v mřížce vlastností.|
|*Pro TypeArgument*|Pravda|Typ T položek obsažených v <xref:System.Collections.Generic.ICollection%601> . Ve výchozím nastavení je tento typ *pro TypeArgument* nastaven na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu *pro TypeArgument* v poli se seznamem v mřížce vlastností.|

## <a name="see-also"></a>Viz také

- [Kolekce](../workflow-designer/collection-activity-designers.md)
- [\<T>Návrhář aktivity AddToCollection](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
