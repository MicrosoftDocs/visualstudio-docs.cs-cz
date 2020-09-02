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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663360"
---
# <a name="rethrow-activity-designer"></a>Návrhář aktivity Rethrow
Návrhář aktivity opětovného **vyvolání** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.Rethrow> aktivity.

## <a name="the-rethrow-activity"></a>Aktivita opětovného vyvolání
 <xref:System.Activities.Statements.Rethrow>Aktivita vyvolá dříve vyvolanou výjimku. Tuto aktivitu lze použít pouze v <xref:System.Activities.Statements.Catch> obslužné rutině v <xref:System.Activities.Statements.TryCatch> aktivitě.

### <a name="using-the-rethrow-activity-designer"></a>Pomocí návrháře aktivity opětovného vyvolání
 Návrhář aktivity opětovného **vyvolání** lze najít v kategorii **zpracování chyb** v **sadě nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář aktivity opětovného **vyvolání** lze přetáhnout ze **sady nástrojů** a [!INCLUDE[wfd2](../includes/wfd2-md.md)] umístit na plochu, kde jsou obvykle umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.Rethrow> aktivita s výchozím **zobrazovaným** parametrem throw. <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity opětovného **vyvolání** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-rethrow-properties"></a>Vlastnosti opětovného vyvolání
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Rethrow> vlastnosti a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje nepovinný popisný název <xref:System.Activities.Statements.Rethrow> aktivity. Výchozí hodnota je znovu vyvolána.|

## <a name="see-also"></a>Viz také
 [Kolekce](../workflow-designer/collection-activity-designers.md) [throw](../workflow-designer/throw-activity-designer.md) [TryCatch](../workflow-designer/trycatch-activity-designer.md)