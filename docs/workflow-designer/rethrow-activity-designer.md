---
title: Návrhář aktivity Rethrow Návrhář postupu provádění
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cb73a674e702d54f970c5dea7ec051f100382c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114749"
---
# <a name="rethrow-activity-designer"></a>Návrhář aktivity Rethrow

Návrhář aktivity opětovného **vyvolání** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.Rethrow> aktivity.

## <a name="the-rethrow-activity"></a>Aktivita opětovného vyvolání

<xref:System.Activities.Statements.Rethrow>Aktivita vyvolá dříve vyvolanou výjimku. Tuto aktivitu lze použít pouze v <xref:System.Activities.Statements.Catch> obslužné rutině v <xref:System.Activities.Statements.TryCatch> aktivitě.

### <a name="use-the-rethrow-activity-designer"></a>Použití návrháře aktivity opětovného vyvolání

Přístup k Návrháři aktivity opětovného **vyvolání** v kategorii **zpracování chyb** sady **nástrojů**. Návrhář aktivity opětovného **vyvolání** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Vyřazení návrháře aktivit vytvoří <xref:System.Activities.Statements.Rethrow> aktivitu s výchozím **názvem DisplayName** . <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity opětovného **vyvolání** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-rethrow-properties"></a>Vlastnosti opětovného vyvolání

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Rethrow> vlastnosti a popisuje, jak se používají v Návrháři:

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje nepovinný popisný název <xref:System.Activities.Statements.Rethrow> aktivity. Výchozí hodnota je znovu vyvolána.|

## <a name="see-also"></a>Viz také

- [Kolekce](../workflow-designer/collection-activity-designers.md)
- [Vyvolá](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
