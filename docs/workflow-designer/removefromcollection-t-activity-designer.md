---
title: '&lt; &gt; Návrhář aktivity RemoveFromCollection T'
description: V Návrhář postupu provádění se naučíte, jak pomocí <T> Návrháře aktivity RemoveFromCollection vytvořit a nakonfigurovat <T> aktivitu RemoveFromCollection.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fdaf7172c00d80e5e7615bfcadcc1fb6233c257
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847359"
---
# <a name="removefromcollectiont-activity-designer"></a>Návrhář aktivity RemoveFromCollection\<T>

Návrhář **aktivity \<T> RemoveFromCollection** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.RemoveFromCollection%601> aktivity.

## <a name="the-removefromcollectiontactivity"></a>Aktivita RemoveFromCollection \<T>

<xref:System.Activities.Statements.RemoveFromCollection%601>Aktivita Odebere zadanou položku z konkrétní kolekce.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Pomocí \<T> Návrháře aktivity RemoveFromCollection

Přihlaste se k Návrháři aktivity **\<T> RemoveFromCollection** v kategorii **kolekce** sady **nástrojů**.
Návrhář **aktivity \<T> RemoveFromCollection** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.RemoveFromCollection%601> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection<Int32 \> . <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity **RemoveFromCollection<T \>** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti je nutné upravit v mřížce vlastností.

### <a name="the-removefromcollectiont-properties"></a>Vlastnosti RemoveFromCollection<T \>

Následující tabulka uvádí <xref:System.Activities.Statements.RemoveFromCollection%601> vlastnosti a popisuje, jak se používají v Návrháři:

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Volitelný popisný název <xref:System.Activities.Statements.RemoveFromCollection%601> aktivity. Výchozí hodnota je RemoveFromCollection<Int32 \> .<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Ano|Položka, která se má odebrat **z \<T> kolekce**. Tato položka je typu *T*, který je typu *pro TypeArgument*. Chcete-li zadat položku, zadejte výraz Visual Basic v mřížce vlastností.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Ano|Kolekce, ze které má být položka odebrána Tato kolekce je typu **ICollection<pro TypeArgument \> .** Chcete-li zadat kolekci, zadejte výraz Visual Basic v mřížce vlastností.|
|*Pro TypeArgument*|Ano|Typ T položek obsažených v <xref:System.Collections.Generic.ICollection%601> . Ve výchozím nastavení je tento typ *pro TypeArgument* nastaven na hodnotu **Int32**. Chcete-li změnit typ, změňte hodnotu *pro TypeArgument* v poli se seznamem v mřížce vlastností.|
|<xref:System.Activities.Activity%601.Result%2A>|Ne|Hodnota, která označuje, zda byla zadaná položka odebrána z kolekce. Chcete-li zadat proměnnou pro svázání s výsledkem, zadejte proměnnou v mřížce vlastností.|

## <a name="see-also"></a>Viz také

- [Kolekce](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)