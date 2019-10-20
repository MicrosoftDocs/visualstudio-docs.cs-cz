---
title: Návrhář aktivity potvrzení Návrhář postupu provádění
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd17f71ff9e408c48493dc862dfe94f8d7037903
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650632"
---
# <a name="confirm-activity-designer"></a>Návrhář aktivity Confirm

Návrhář aktivity **potvrzení** se používá k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.Confirm>.

## <a name="the-confirm-activity"></a>Aktivita potvrzení
 Aktivita <xref:System.Activities.Statements.Confirm> explicitně vyvolá <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> pro aktivitu obsaženou v <xref:System.Activities.Statements.CompensableActivity>. Pokud se aktivita <xref:System.Activities.Statements.Confirm> nepoužívá v <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> nebo <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity>, musíte zadat vlastnost <xref:System.Activities.Statements.Confirm.Target%2A>.

 @No__t_0 určené <xref:System.Activities.Statements.Compensate.Target%2A> poskytuje způsob, jak explicitně potvrdit nebo kompenzovat <xref:System.Activities.Statements.CompensableActivity> po úspěšném dokončení <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-confirm-activity-designer"></a>Použití návrháře aktivit pro potvrzení
 Návrháře **potvrzení** aktivity lze najít v kategorii **transakce** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** +**ALT** +**X**.

 Návrháře **potvrzení** aktivity lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.Confirm> s výchozím <xref:System.Activities.Activity.DisplayName%2A> potvrzení. Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit buď v záhlaví návrháře **potvrzení** aktivity, nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-confirm-properties"></a>Vlastnosti Confirm
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.Confirm> a popisuje, jak se používají v návrháři. Vlastnost <xref:System.Activities.Activity.DisplayName%2A> lze upravit v mřížce vlastností nebo na Návrhář postupu provádění povrchu, ale vlastnost <xref:System.Activities.Statements.Confirm.Target%2A> musí být upravena v mřížce vlastností.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje nepovinný popisný název aktivity <xref:System.Activities.Statements.CancellationScope>. Výchozí hodnota je potvrdit.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Podmínka|Určuje <xref:System.Activities.InArgument%601>, který obsahuje <xref:System.Activities.Statements.CompensationToken> pro tuto <xref:System.Activities.Statements.Confirm> aktivitu.|

## <a name="see-also"></a>Viz také:

- [Transakce](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)