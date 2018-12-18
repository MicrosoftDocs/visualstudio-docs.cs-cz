---
title: Návrhář aktivity Compensate návrháře postupu provádění-
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed306b6665919101c682f2f541f5b5ef693d2b58
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909832"
---
# <a name="compensate-activity-designer"></a>Návrhář aktivity Compensate

**Kompenzace** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.Activities.Statements.Compensate> aktivity.

## <a name="the-compensate-activity"></a>Aktivitu kompenzace

<xref:System.Activities.Statements.Compensate> Explicitně vyvolá aktivitu <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> pro aktivitu součástí <xref:System.Activities.Statements.CompensableActivity>. Pokud <xref:System.Activities.Statements.Compensate> aktivity se nepoužívá v rámci <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, nebo <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> z <xref:System.Activities.Statements.CompensableActivity>, pak je nutné zadat <xref:System.Activities.Statements.Compensate.Target%2A> vlastnost.

<xref:System.Activities.Statements.CompensationToken> Určená <xref:System.Activities.Statements.Compensate.Target%2A> zajišťuje explicitně potvrdit nebo kompenzaci <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> byla úspěšně dokončena.

### <a name="using-the-compensate-activity-designer"></a>Použití Návrhář aktivity Compensate

**Kompenzace** návrháře aktivit najdete v **transakce** kategorii **nástrojů**. Chcete-li otevřít **nástrojů**, vyberte **nástrojů** karty na levé straně návrháře postupu provádění. Můžete také vybrat **nástrojů** z **zobrazení** nabídky nebo stisknutím klávesy **Ctrl**+**Alt** + **X**.

**Kompenzace** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění bez ohledu na to aktivity jsou umístěny, například jako uvnitř <xref:System.Activities.Statements.Sequence>. Vyřazení Návrhář aktivity vytvoří <xref:System.Activities.Statements.Compensate> aktivity s výchozím <xref:System.Activities.Activity.DisplayName%2A> z kompenzace. <xref:System.Activities.Activity.DisplayName%2A> Hodnota se dá upravit v záhlaví **kompenzace** Návrhář aktivity nebo **DisplayName** pole mřížky vlastností.

### <a name="the-compensate-properties"></a>Kompenzaci vlastnosti

Následující tabulka ukazuje <xref:System.Activities.Statements.CancellationScope> vlastnosti a popisuje, jak se používají v návrháři. <xref:System.Activities.Activity.DisplayName%2A> Vlastnost lze upravit v mřížce vlastností nebo na plochu návrháře postupu provádění. Upravit <xref:System.Activities.Statements.Compensate.Target%2A> vlastnost v mřížce vlastností.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje volitelný popisný název <xref:System.Activities.Statements.Compensate> aktivity. Výchozí hodnota je kompenzace.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Hodnota TRUE|Určuje <xref:System.Activities.InArgument%601> , který obsahuje <xref:System.Activities.Statements.CompensationToken> to <xref:System.Activities.Statements.Compensate> aktivity.|

## <a name="see-also"></a>Viz také:

- [Transakce](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Návrhář aktivity Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)