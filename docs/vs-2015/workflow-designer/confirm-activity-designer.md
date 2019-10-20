---
title: Návrhář aktivity potvrdit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b3835c6cb537e7ac74862ac4a6794dd7b0bd5003
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656961"
---
# <a name="confirm-activity-designer"></a>Návrhář aktivity Confirm
Návrhář aktivity **potvrzení** se používá k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.Confirm>.

## <a name="the-confirm-activity"></a>Aktivita potvrzení
 Aktivita <xref:System.Activities.Statements.Confirm> explicitně vyvolá <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> pro aktivitu obsaženou v <xref:System.Activities.Statements.CompensableActivity>. Pokud se aktivita <xref:System.Activities.Statements.Confirm> nepoužívá v <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> nebo <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity>, musíte zadat vlastnost <xref:System.Activities.Statements.Confirm.Target%2A>.

 @No__t_0 určené <xref:System.Activities.Statements.Compensate.Target%2A> poskytuje způsob, jak explicitně potvrdit nebo kompenzovat <xref:System.Activities.Statements.CompensableActivity> po úspěšném dokončení <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-confirm-activity-designer"></a>Použití návrháře aktivit pro potvrzení
 Návrháře **potvrzení** aktivity lze najít v kategorii **transakce** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v **zobrazení).** v nabídce nebo CTRL + ALT + X.)

 Návrháře **potvrzení** aktivity lze přetáhnout ze **sady nástrojů** a přetáhnout na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.Confirm> s výchozím <xref:System.Activities.Activity.DisplayName%2A> potvrzení. Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit buď v záhlaví návrháře **potvrzení** aktivity, nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-confirm-properties"></a>Vlastnosti Confirm
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.Confirm> a popisuje, jak se používají v návrháři. Vlastnost <xref:System.Activities.Activity.DisplayName%2A> lze upravit v mřížce vlastností nebo na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu, ale vlastnost <xref:System.Activities.Statements.Confirm.Target%2A> musí být upravena v mřížce vlastností.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje nepovinný popisný název aktivity <xref:System.Activities.Statements.CancellationScope>. Výchozí hodnota je potvrdit.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Podmínka|Určuje <xref:System.Activities.InArgument%601>, který obsahuje <xref:System.Activities.Statements.CompensationToken> pro tuto <xref:System.Activities.Statements.Confirm> aktivitu.|

## <a name="see-also"></a>Viz také
 [](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [transakce aktivita CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [kompenzuje](../workflow-designer/compensate-activity-designer.md) [objekt TransactionScope](../workflow-designer/transactionscope-activity-designer.md)