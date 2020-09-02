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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656961"
---
# <a name="confirm-activity-designer"></a>Návrhář aktivity Confirm
Návrhář **potvrzení** aktivity se používá k vytvoření a konfiguraci <xref:System.Activities.Statements.Confirm> aktivity.

## <a name="the-confirm-activity"></a>Aktivita potvrzení
 <xref:System.Activities.Statements.Confirm>Aktivita explicitně vyvolá aktivitu, která je <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> obsažena v <xref:System.Activities.Statements.CompensableActivity> . Pokud se <xref:System.Activities.Statements.Confirm> aktivita nepoužívá v rámci <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> nebo, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity> musíte zadat <xref:System.Activities.Statements.Confirm.Target%2A> vlastnost.

 <xref:System.Activities.Statements.CompensationToken>Zadaný pomocí <xref:System.Activities.Statements.Compensate.Target%2A> poskytuje způsob, jak explicitně potvrdit nebo kompenzovat <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> úspěšném dokončení.

### <a name="using-the-confirm-activity-designer"></a>Použití návrháře aktivit pro potvrzení
 Návrháře **potvrzení** aktivity lze najít v kategorii **transakce** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrháře **potvrzení** aktivity lze přetáhnout ze **sady nástrojů** a [!INCLUDE[wfd2](../includes/wfd2-md.md)] umístit na plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.Confirm> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> Confirm. <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit buď v záhlaví návrháře **potvrzení** aktivity, nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-confirm-properties"></a>Vlastnosti Confirm
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Confirm> vlastnosti a popisuje, jak se používají v návrháři. <xref:System.Activities.Activity.DisplayName%2A>Vlastnost se dá upravovat v mřížce vlastností nebo na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu, ale vlastnost se <xref:System.Activities.Statements.Confirm.Target%2A> musí upravovat v mřížce vlastností.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje nepovinný popisný název <xref:System.Activities.Statements.CancellationScope> aktivity. Výchozí hodnota je potvrdit.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Ano|Určuje <xref:System.Activities.InArgument%601> , který obsahuje <xref:System.Activities.Statements.CompensationToken> pro tuto <xref:System.Activities.Statements.Confirm> aktivitu.|

## <a name="see-also"></a>Viz také
 [Transaction](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [transakce aktivita CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [kompenzuje](../workflow-designer/compensate-activity-designer.md) [objekt TransactionScope](../workflow-designer/transactionscope-activity-designer.md)