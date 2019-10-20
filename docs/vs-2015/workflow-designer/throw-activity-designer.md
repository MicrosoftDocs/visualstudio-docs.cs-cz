---
title: Návrhář aktivity throw | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1855daa5016241fb6eb04f05d7218e02083fc0a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655154"
---
# <a name="throw-activity-designer"></a>Návrhář aktivity Throw
Návrhář aktivity **throw** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.Throw>.

## <a name="the-throw-activity"></a>Aktivita throw
 Aktivita <xref:System.Activities.Statements.Throw> vyvolá výjimku.

### <a name="using-the-throw-activity-designer"></a>Použití návrháře aktivity throw
 Návrhář aktivity **throw** lze najít v kategorii **zpracování chyb** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v **zobrazení).** nebo CTRL + ALT + X.)

 Návrhář aktivity **throw** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.Throw> s výchozím **zobrazovaným názvem** pro vyvolání. Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře aktivit **throw** nebo v poli **DisplayName** v mřížce vlastností. Vlastnost <xref:System.Activities.Statements.Throw.Exception%2A> musí být upravena v mřížce vlastností.

### <a name="the-throw-properties"></a>Vlastnosti throw
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.Throw> a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje nepovinný popisný název aktivity <xref:System.Activities.Statements.Throw>. Výchozí hodnota je throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Podmínka|Výjimka, která se má vyvolat Tato výjimka musí být odvozena od <xref:System.Exception>. Chcete-li zadat výjimku, zadejte výraz Visual Basic v mřížce vlastností.|

## <a name="see-also"></a>Viz také
 Opětovné vyvolání [kolekce](../workflow-designer/collection-activity-designers.md) [](../workflow-designer/rethrow-activity-designer.md) [throw Activity Designer](../workflow-designer/throw-activity-designer.md) [TryCatch](../workflow-designer/trycatch-activity-designer.md)