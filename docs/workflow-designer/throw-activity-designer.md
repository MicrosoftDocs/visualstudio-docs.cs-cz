---
title: Návrhář postupu provádění – Návrhář aktivity throw
description: Přečtěte si o aktivitě throw a o tom, jak můžete pomocí nástroje throw Activity Designer vytvořit a nakonfigurovat aktivitu throw.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a1ffd0a9dda243e53431e419910b866853cd3932
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969096"
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
