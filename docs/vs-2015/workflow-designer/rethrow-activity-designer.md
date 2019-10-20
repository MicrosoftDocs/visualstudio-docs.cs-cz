---
title: Návrhář aktivity opětovného vyvolání | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c65469242a60c64d6f31bfaea4fdbbf2d5251a34
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663360"
---
# <a name="rethrow-activity-designer"></a>Návrhář aktivity Rethrow
Návrhář aktivity opětovného **vyvolání** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.Rethrow>.

## <a name="the-rethrow-activity"></a>Aktivita opětovného vyvolání
 Aktivita <xref:System.Activities.Statements.Rethrow> vyvolá dříve vyvolanou výjimku. Tuto aktivitu lze použít pouze v obslužné rutině <xref:System.Activities.Statements.Catch> v aktivitě <xref:System.Activities.Statements.TryCatch>.

### <a name="using-the-rethrow-activity-designer"></a>Pomocí návrháře aktivity opětovného vyvolání
 Návrhář aktivity opětovného **vyvolání** lze najít v kategorii **zpracování chyb** v **sadě nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte **panel nástrojů** z  **Zobrazit** nabídku nebo CTRL + ALT + X.)

 Návrhář aktivity opětovného **vyvolání** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.Rethrow> s výchozím **zobrazovaným názvem** pro vyvolání. Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře aktivity opětovného **vyvolání** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-rethrow-properties"></a>Vlastnosti opětovného vyvolání
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.Rethrow> a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje nepovinný popisný název aktivity <xref:System.Activities.Statements.Rethrow>. Výchozí hodnota je znovu vyvolána.|

## <a name="see-also"></a>Viz také
 [Kolekce](../workflow-designer/collection-activity-designers.md) [throw](../workflow-designer/throw-activity-designer.md) [TryCatch](../workflow-designer/trycatch-activity-designer.md)