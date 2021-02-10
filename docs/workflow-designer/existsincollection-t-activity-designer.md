---
title: '&lt; &gt; Návrhář aktivity ExistsInCollection T'
description: Přečtěte si, jak můžete pomocí <T> Návrháře aktivity ExistsInCollection v Návrhář postupu provádění vytvořit a nakonfigurovat aktivitu ExistsInCollection <T> .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 971d6bd028315ae4a8b6f3a88164c97c6f95712b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961323"
---
# <a name="existsincollectiont-activity-designer"></a>Návrhář aktivity ExistsInCollection\<T>

Návrhář **aktivity \<T> ExistsInCollection** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.ExistsInCollection%601> aktivity.

## <a name="the-existsincollectiont-activity"></a>Aktivita ExistsInCollection \<T>

<xref:System.Activities.Statements.ExistsInCollection%601>Aktivita určuje, zda zadaná položka existuje v určité kolekci.

### <a name="using-the-existsincollectiont-activity-designer"></a>Pomocí \<T> Návrháře aktivity ExistsInCollection

Návrhář **aktivity \<T> ExistsInCollection** lze najít v kategorii **kolekce** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** + **+** + **X**.

Návrhář **aktivity \<T> ExistsInCollection** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.ExistsInCollection%601> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection<Int32 \> . (Ve výchozím nastavení je *pro TypeArgument* typu **Int32**. Dá se změnit v mřížce vlastností.)  <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity **ExistsInCollection<T \>** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti je nutné upravit v mřížce vlastností.

### <a name="the-existsincollectiont-properties"></a>Vlastnosti ExistsInCollection \<T>

Následující tabulka uvádí <xref:System.Activities.Statements.ExistsInCollection%601> vlastnosti a popisuje, jak se používají v Návrháři:

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.ExistsInCollection%601> aktivity Výchozí hodnota je ExistsInCollection<Int32 \> . I když není <xref:System.Activities.Activity.DisplayName%2A> hodnota striktně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Ano|Položka, která se má hledat \<T> v kolekci Tato položka je typu *T*, který je typu *pro TypeArgument*. Chcete-li zadat položku, zadejte výraz Visual Basic v mřížce vlastností.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Ano|Kolekce, ve které se má zjistit, jestli položka existuje Tato kolekce je typu **ICollection<pro TypeArgument \> .** Chcete-li zadat kolekci, zadejte výraz Visual Basic v mřížce vlastností.|
|*Pro TypeArgument*|Ano|Typ T položek obsažených v <xref:System.Collections.Generic.ICollection%601> . Ve výchozím nastavení je tento typ *pro TypeArgument* nastaven na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu *pro TypeArgument* v poli se seznamem v mřížce vlastností.|
|<xref:System.Activities.Activity%601.Result%2A>|Ne|Hodnota, která označuje, zda zadaná položka v kolekci existuje. Chcete-li zadat proměnnou pro svázání s výsledkem, zadejte Visual Basic proměnnou v mřížce vlastností.|

## <a name="see-also"></a>Viz také

- [Kolekce](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)