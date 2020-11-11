---
title: Návrhář aktivity potvrzení Návrhář postupu provádění
description: Přečtěte si informace o návrháři aktivity pro potvrzení a o tom, jak můžete pomocí tohoto návrháře vytvořit a nakonfigurovat aktivitu Confirm.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4928dcd7a9e1b83ba797614545315022d0f36ac3
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438149"
---
# <a name="confirm-activity-designer"></a>Návrhář aktivity Confirm

Návrhář **potvrzení** aktivity se používá k vytvoření a konfiguraci <xref:System.Activities.Statements.Confirm> aktivity.

## <a name="the-confirm-activity"></a>Aktivita potvrzení
 <xref:System.Activities.Statements.Confirm>Aktivita explicitně vyvolá aktivitu, která je <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> obsažena v <xref:System.Activities.Statements.CompensableActivity> . Pokud se <xref:System.Activities.Statements.Confirm> aktivita nepoužívá v rámci <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> nebo, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity> musíte zadat <xref:System.Activities.Statements.Confirm.Target%2A> vlastnost.

 <xref:System.Activities.Statements.CompensationToken>Zadaný pomocí <xref:System.Activities.Statements.Compensate.Target%2A> poskytuje způsob, jak explicitně potvrdit nebo kompenzovat <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> úspěšném dokončení.

### <a name="using-the-confirm-activity-designer"></a>Použití návrháře aktivit pro potvrzení
 Návrháře **potvrzení** aktivity lze najít v kategorii **transakce** sady **nástrojů** , ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** + **+** + **X**.

 Návrháře **potvrzení** aktivity lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.Confirm> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> Confirm. <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit buď v záhlaví návrháře **potvrzení** aktivity, nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-confirm-properties"></a>Vlastnosti Confirm
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Confirm> vlastnosti a popisuje, jak se používají v návrháři. <xref:System.Activities.Activity.DisplayName%2A>Vlastnost lze upravit v mřížce vlastností nebo na Návrhář postupu provádění povrchu, ale <xref:System.Activities.Statements.Confirm.Target%2A> vlastnost je třeba upravit v mřížce vlastností.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Určuje nepovinný popisný název <xref:System.Activities.Statements.CancellationScope> aktivity. Výchozí hodnota je potvrdit.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Pravda|Určuje <xref:System.Activities.InArgument%601> , který obsahuje <xref:System.Activities.Statements.CompensationToken> pro tuto <xref:System.Activities.Statements.Confirm> aktivitu.|

## <a name="see-also"></a>Viz také

- [Transakce](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)