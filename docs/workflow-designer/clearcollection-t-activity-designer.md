---
title: Návrhář postupu provádění – Clear &lt; &gt; Návrhář aktivitycollection T
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 710e221441736ecb2415aec32c7f0bfb9a2d99ac
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711622"
---
# <a name="clearcollectiont-activity-designer"></a>Návrhář aktivity ClearCollection\<T>

Návrhář aktivity **ClearCollection \<T> ** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.ClearCollection%601> aktivity.

## <a name="the-clearcollectiont-activity"></a>Aktivita ClearCollection \<T>

Tato <xref:System.Activities.Statements.ClearCollection%601> Aktivita vymaže zadanou kolekci všech položek.

### <a name="using-the-clearcollectiont-activity-designer"></a>Pomocí \<T> návrháře aktivit ClearCollection

Návrhář **aktivity ClearCollection \<T> ** lze najít v kategorii **kolekce** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** + **+** + **X**.

Návrhář aktivity **ClearCollection \<T> ** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Vyřazení návrháře aktivit vytvoří <xref:System.Activities.Statements.ClearCollection%601> aktivitu s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> clearcollection<Int32 \> . (Ve výchozím nastavení je *pro TypeArgument* typu **Int32**. Pro TypeArgument lze změnit v mřížce vlastností.) <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity **clearcollection<\> T** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti je nutné upravit v mřížce vlastností.

### <a name="the-clearcollectiont-properties"></a>Vlastnosti ClearCollection \<T>

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.ClearCollection%601> vlastnosti a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje nepovinný popisný název <xref:System.Activities.Statements.ClearCollection%601> aktivity. Výchozí hodnota je ClearCollection<Int32 \> . I když není <xref:System.Activities.Activity.DisplayName%2A> hodnota striktně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Ano|Určuje kolekci, do které mají být položky vymazány. Tato kolekce je typu **ICollection \<TypeArgument> .** Chcete-li zadat kolekci, zadejte výraz Visual Basic v mřížce vlastností.|
|*Pro TypeArgument*|Ano|Určuje typ T položek obsažených v <xref:System.Collections.Generic.ICollection%601> . Ve výchozím nastavení je tento typ *pro TypeArgument* nastaven na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu *pro TypeArgument* v poli se seznamem v mřížce vlastností.|

## <a name="see-also"></a>Viz také:

- [Kolekce](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)