---
title: Návrhář postupu provádění – Návrhář aktivity throw
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 650082ab0e4f8576b7028b8011c88bf5d93b2afd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593093"
---
# <a name="throw-activity-designer"></a>Návrhář aktivity Throw

Návrhář aktivity **throw** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.Throw> aktivity.

## <a name="the-throw-activity"></a>Aktivita throw

<xref:System.Activities.Statements.Throw>Aktivita vyvolá výjimku.

### <a name="using-the-throw-activity-designer"></a>Použití návrháře aktivity throw

Přístup k Návrháři aktivity **throw** v kategorii **zpracování chyb** sady **nástrojů**.

Návrhář aktivity **throw** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.Throw> aktivita s výchozím **zobrazovaným** parametrem throw. <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity **throw** nebo v poli **DisplayName** v mřížce vlastností. <xref:System.Activities.Statements.Throw.Exception%2A>Vlastnost musí být upravena v mřížce vlastností.

### <a name="the-throw-properties"></a>Vlastnosti throw

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Throw> vlastnosti a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje nepovinný popisný název <xref:System.Activities.Statements.Throw> aktivity. Výchozí hodnota je throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Ano|Výjimka, která se má vyvolat Tato výjimka musí být odvozena z <xref:System.Exception> . Chcete-li zadat výjimku, zadejte výraz Visual Basic v mřížce vlastností.|

## <a name="see-also"></a>Viz také

- [Kolekce](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Návrhář aktivity Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
