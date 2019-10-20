---
title: Návrhář aktivity Rethrow Návrhář postupu provádění
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d015ad500537a17cfc2c48c8076df43a38534ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650007"
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
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje nepovinný popisný název aktivity <xref:System.Activities.Statements.Rethrow>. Výchozí hodnota je znovu vyvolána.|

## <a name="see-also"></a>Viz také:

- [Kolekce](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)