---
title: Návrhář aktivity Návrhář postupu provádění – náhrada
description: Přečtěte si informace o nástroji pro vytváření kompenzací a o tom, jak můžete pomocí návrháře aktivity kompenzace vytvořit a nakonfigurovat aktivitu kompenzace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 36ab20854adb952d098f71904cdd3cb092e27ac9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955681"
---
# <a name="compensate-activity-designer"></a>Návrhář aktivity Compensate

Návrhář aktivity **kompenzace** se používá k vytvoření a konfiguraci <xref:System.Activities.Statements.Compensate> aktivity.

## <a name="the-compensate-activity"></a>Aktivita kompenzace

<xref:System.Activities.Statements.Compensate>Aktivita explicitně vyvolá aktivitu, která je <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> obsažena v <xref:System.Activities.Statements.CompensableActivity> . Pokud se <xref:System.Activities.Statements.Compensate> aktivita nepoužívá v rámci <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> nebo, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity> musíte zadat <xref:System.Activities.Statements.Compensate.Target%2A> vlastnost.

<xref:System.Activities.Statements.CompensationToken>Zadaný pomocí <xref:System.Activities.Statements.Compensate.Target%2A> poskytuje způsob, jak explicitně potvrdit nebo kompenzovat <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> úspěšném dokončení.

### <a name="using-the-compensate-activity-designer"></a>Pomocí návrháře aktivity kompenzace

Návrhář aktivity **kompenzace** lze najít v kategorii **transakce** sady **nástrojů**. Chcete-li otevřít **sadu nástrojů**, vyberte kartu **panelu nástrojů** na levé straně Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** + **+** + **X**.

Návrhář aktivity **kompenzace** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Vyřazení návrháře aktivit vytvoří <xref:System.Activities.Statements.Compensate> aktivitu s výchozí <xref:System.Activities.Activity.DisplayName%2A> kompenzací. <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity **kompenzace** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-compensate-properties"></a>Vlastnosti kompenzace

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.CancellationScope> vlastnosti a popisuje, jak se používají v návrháři. <xref:System.Activities.Activity.DisplayName%2A>Vlastnost lze upravit v mřížce vlastností nebo na Návrhář postupu provádění Surface. Upravte <xref:System.Activities.Statements.Compensate.Target%2A> vlastnost v mřížce vlastností.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje nepovinný popisný název <xref:System.Activities.Statements.Compensate> aktivity. Výchozí hodnota je kompenzovat.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Ano|Určuje <xref:System.Activities.InArgument%601> , který obsahuje <xref:System.Activities.Statements.CompensationToken> pro tuto <xref:System.Activities.Statements.Compensate> aktivitu.|

## <a name="see-also"></a>Viz také

- [Transakce](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Návrhář aktivity Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)