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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114749"
---
# <a name="rethrow-activity-designer"></a>Návrhář aktivity Rethrow

Návrhář aktivity opětovného **vyvolání** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.Rethrow>.

## <a name="the-rethrow-activity"></a>Aktivita opětovného vyvolání

Aktivita <xref:System.Activities.Statements.Rethrow> vyvolá dříve vyvolanou výjimku. Tuto aktivitu lze použít pouze v obslužné rutině <xref:System.Activities.Statements.Catch> v aktivitě <xref:System.Activities.Statements.TryCatch>.

### <a name="use-the-rethrow-activity-designer"></a>Použití návrháře aktivity opětovného vyvolání

Přístup k Návrháři aktivity opětovného **vyvolání** v kategorii **zpracování chyb** sady **nástrojů**. Návrhář aktivity opětovného **vyvolání** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Vyřazení návrháře aktivit vytvoří aktivitu <xref:System.Activities.Statements.Rethrow> s výchozím **názvem DisplayName** . Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře aktivity opětovného **vyvolání** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-rethrow-properties"></a>Vlastnosti opětovného vyvolání

Následující tabulka ukazuje vlastnosti <xref:System.Activities.Statements.Rethrow> a popisuje, jak se používají v Návrháři:

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Určuje nepovinný popisný název aktivity <xref:System.Activities.Statements.Rethrow>. Výchozí hodnota je znovu vyvolána.|

## <a name="see-also"></a>Viz také:

- [Kolekce](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
