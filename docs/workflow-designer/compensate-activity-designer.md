---
title: Návrhář aktivity Návrhář postupu provádění – náhrada
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65203663214e6bc82a4a7b20af9caa25bfd98ee4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650658"
---
# <a name="compensate-activity-designer"></a>Návrhář aktivity Compensate

Návrhář aktivity **kompenzace** se používá k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.Compensate>.

## <a name="the-compensate-activity"></a>Aktivita kompenzace

Aktivita <xref:System.Activities.Statements.Compensate> explicitně vyvolá <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> pro aktivitu obsaženou v <xref:System.Activities.Statements.CompensableActivity>. Pokud se aktivita <xref:System.Activities.Statements.Compensate> nepoužívá v <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> nebo <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity>, musíte zadat vlastnost <xref:System.Activities.Statements.Compensate.Target%2A>.

@No__t_0 určené <xref:System.Activities.Statements.Compensate.Target%2A> poskytuje způsob, jak explicitně potvrdit nebo kompenzovat <xref:System.Activities.Statements.CompensableActivity> po úspěšném dokončení <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-compensate-activity-designer"></a>Pomocí návrháře aktivity kompenzace

Návrhář aktivity **kompenzace** lze najít v kategorii **transakce** sady **nástrojů**. Chcete-li otevřít **sadu nástrojů**, vyberte kartu **panelu nástrojů** na levé straně Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** +**ALT** +**X**.

Návrhář aktivity **kompenzace** je možné přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Vyřazení návrháře aktivit vytvoří aktivitu <xref:System.Activities.Statements.Compensate> s výchozí <xref:System.Activities.Activity.DisplayName%2A>ou kompenzací. Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře aktivity **kompenzace** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-compensate-properties"></a>Vlastnosti kompenzace

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.CancellationScope> a popisuje, jak se používají v návrháři. Vlastnost <xref:System.Activities.Activity.DisplayName%2A> lze upravit v mřížce vlastností nebo na Návrhář postupu provádění povrchu. Upravte vlastnost <xref:System.Activities.Statements.Compensate.Target%2A> v mřížce vlastností.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje nepovinný popisný název aktivity <xref:System.Activities.Statements.Compensate>. Výchozí hodnota je kompenzovat.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Podmínka|Určuje <xref:System.Activities.InArgument%601>, který obsahuje <xref:System.Activities.Statements.CompensationToken> pro tuto <xref:System.Activities.Statements.Compensate> aktivitu.|

## <a name="see-also"></a>Viz také:

- [Transakce](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Návrhář aktivity Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)