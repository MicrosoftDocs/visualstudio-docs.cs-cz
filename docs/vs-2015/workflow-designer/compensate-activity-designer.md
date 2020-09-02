---
title: Návrhář aktivity kompenzace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 706cd446e931d6a3a065a3e8abfb58b5a90e9152
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656980"
---
# <a name="compensate-activity-designer"></a>Návrhář aktivity Compensate
Návrhář aktivity **kompenzace** se používá k vytvoření a konfiguraci <xref:System.Activities.Statements.Compensate> aktivity.

## <a name="the-compensate-activity"></a>Aktivita kompenzace
 <xref:System.Activities.Statements.Compensate>Aktivita explicitně vyvolá aktivitu, která je <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> obsažena v <xref:System.Activities.Statements.CompensableActivity> . Pokud se <xref:System.Activities.Statements.Compensate> aktivita nepoužívá v rámci <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> nebo, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity> musíte zadat <xref:System.Activities.Statements.Compensate.Target%2A> vlastnost.

 <xref:System.Activities.Statements.CompensationToken>Zadaný pomocí <xref:System.Activities.Statements.Compensate.Target%2A> poskytuje způsob, jak explicitně potvrdit nebo kompenzovat <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> úspěšném dokončení.

### <a name="using-the-compensate-activity-designer"></a>Pomocí návrháře aktivity kompenzace
 Návrhář aktivity **kompenzace** se dá najít v kategorii **transakce** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář aktivity **kompenzace** je možné přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.Compensate> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> kompenzace. <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity **kompenzace** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-compensate-properties"></a>Vlastnosti kompenzace
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.CancellationScope> vlastnosti a popisuje, jak se používají v návrháři. <xref:System.Activities.Activity.DisplayName%2A>Vlastnost se dá upravovat v mřížce vlastností nebo na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu, ale vlastnost se <xref:System.Activities.Statements.Compensate.Target%2A> musí upravovat v mřížce vlastností.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje nepovinný popisný název <xref:System.Activities.Statements.Compensate> aktivity. Výchozí hodnota je kompenzovat.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Ano|Určuje <xref:System.Activities.InArgument%601> , který obsahuje <xref:System.Activities.Statements.CompensationToken> pro tuto <xref:System.Activities.Statements.Compensate> aktivitu.|

## <a name="see-also"></a>Viz také
 [Návrhář aktivity kompenzace](../workflow-designer/compensate-activity-designer.md) [transakčního](../workflow-designer/transaction-activity-designers.md) [aktivita compensableactivityu](../workflow-designer/compensableactivity-activity-designer.md) – [potvrzení](../workflow-designer/confirm-activity-designer.md) objektu [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)