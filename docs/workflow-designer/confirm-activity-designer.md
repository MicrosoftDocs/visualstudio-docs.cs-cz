---
title: Návrhář aktivity Confirm návrháře postupu provádění-
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f6823b564b7ec3da1585810c27db2f97c1b16ae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906530"
---
# <a name="confirm-activity-designer"></a>Návrhář aktivity Confirm

**Potvrdit** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.Activities.Statements.Confirm> aktivity.

## <a name="the-confirm-activity"></a>Potvrzení aktivity
 <xref:System.Activities.Statements.Confirm> Explicitně vyvolá aktivitu <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> pro aktivitu součástí <xref:System.Activities.Statements.CompensableActivity>. Pokud <xref:System.Activities.Statements.Confirm> aktivity se nepoužívá v rámci <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, nebo <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> z <xref:System.Activities.Statements.CompensableActivity>, pak je nutné zadat <xref:System.Activities.Statements.Confirm.Target%2A> vlastnost.

 <xref:System.Activities.Statements.CompensationToken> Určená <xref:System.Activities.Statements.Compensate.Target%2A> zajišťuje explicitně potvrdit nebo kompenzaci <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> byla úspěšně dokončena.

### <a name="using-the-confirm-activity-designer"></a>Použití Návrhář aktivity Confirm
 **Potvrdit** návrháře aktivit najdete v **transakce** kategorii **nástrojů**, který přistupuje po kliknutí **nástrojů**karty na levé straně návrháře postupu provádění. Můžete také vybrat **nástrojů** z **zobrazení** nabídky nebo stisknutím klávesy **Ctrl**+**Alt** + **X**.

 **Potvrdit** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění bez ohledu na to aktivity jsou obvykle umístěny, například jako uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří <xref:System.Activities.Statements.Confirm> aktivity s výchozím <xref:System.Activities.Activity.DisplayName%2A> o potvrzení. <xref:System.Activities.Activity.DisplayName%2A> Hodnota může být upravit buď v hlavičce **potvrdit** Návrhář aktivity nebo **DisplayName** pole mřížky vlastností.

### <a name="the-confirm-properties"></a>Potvrzení vlastnosti
 Následující tabulka ukazuje <xref:System.Activities.Statements.Confirm> vlastnosti a popisuje, jak se používají v návrháři. <xref:System.Activities.Activity.DisplayName%2A> Vlastnost lze upravit v mřížce vlastností nebo na plochu návrháře postupu provádění, ale <xref:System.Activities.Statements.Confirm.Target%2A> musí být vlastnost upravit v mřížce vlastností.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje volitelný popisný název <xref:System.Activities.Statements.CancellationScope> aktivity. Výchozí hodnota je potvrzení.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Hodnota TRUE|Určuje <xref:System.Activities.InArgument%601> , který obsahuje <xref:System.Activities.Statements.CompensationToken> to <xref:System.Activities.Statements.Confirm> aktivity.|

## <a name="see-also"></a>Viz také:

- [Transakce](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)