---
title: Návrhář aktivity CancellationScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa41d63fa4f67037a8e98e72abc3e338ad894f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659181"
---
# <a name="cancellationscope-activity-designer"></a>Návrhář aktivity CancellationScope
Návrhář aktivity **CancellationScope** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.CancellationScope> aktivity.

## <a name="the-cancellationscope-activity"></a>Aktivita CancellationScope
 <xref:System.Activities.Statements.CancellationScope>Aktivita umožňuje určit aktivitu pro provádění a logiku zrušení pro danou aktivitu.

### <a name="using-the-cancellationscope-activity-designer"></a>Pomocí návrháře aktivity CancellationScope
 Návrhář aktivity **CancellationScope** se dá najít v kategorii **transakce** sady **nástrojů**, ke které se dostanete tak, že kliknete na kartu **panelu nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář aktivity **CancellationScope** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.CancellationScope> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> CancellationScope. <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity **CancellationScope** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-cancellationscope-properties"></a>Vlastnosti CancellationScope
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.CancellationScope> vlastnosti a popisuje, jak se používají v návrháři. <xref:System.Activities.Activity.DisplayName%2A>Vlastnost se dá upravit v mřížce vlastností, ale ostatní vlastnosti se musí upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Volitelný popisný název <xref:System.Activities.Statements.CancellationScope> aktivity. Výchozí hodnota je CancellationScope. I když není <xref:System.Activities.Activity.DisplayName%2A> hodnota striktně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Ano|Určuje aktivitu, pro kterou je k dispozici logika zrušení. Chcete-li přidat <xref:System.Activities.Statements.CancellationScope.Body%2A> aktivitu, přetáhněte aktivitu ze **sady nástrojů** do pole **text** v Návrháři aktivity **CancellationScope** s textem nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Ano|Určuje aktivitu, která se spustí v případě zrušení. Chcete-li přidat <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> aktivitu, přetáhněte aktivitu ze **sady nástrojů** do pole **CancellationHandler** v Návrháři aktivity **CancellationScope** s textem nápovědy "Sem přetáhněte aktivitu".|

## <a name="see-also"></a>Viz také
 [Transaction](../workflow-designer/transaction-activity-designers.md) [Aktivita CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [Compensate](../workflow-designer/compensate-activity-designer.md) transakce s [potvrzením](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)