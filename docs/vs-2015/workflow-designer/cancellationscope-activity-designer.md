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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659181"
---
# <a name="cancellationscope-activity-designer"></a>Návrhář aktivity CancellationScope
Návrhář aktivity **CancellationScope** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.CancellationScope>.

## <a name="the-cancellationscope-activity"></a>Aktivita CancellationScope
 Aktivita <xref:System.Activities.Statements.CancellationScope> umožňuje určit aktivitu pro provádění a logiku zrušení pro danou aktivitu.

### <a name="using-the-cancellationscope-activity-designer"></a>Pomocí návrháře aktivity CancellationScope
 Návrhář aktivity **CancellationScope** se dá najít v kategorii **transakce** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v **zobrazení).** nebo CTRL + ALT + X.)

 Návrhář aktivity **CancellationScope** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.CancellationScope> s výchozím <xref:System.Activities.Activity.DisplayName%2A> CancellationScope. Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře aktivity **CancellationScope** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-cancellationscope-properties"></a>Vlastnosti CancellationScope
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.CancellationScope> a popisuje, jak se používají v návrháři. Vlastnost <xref:System.Activities.Activity.DisplayName%2A> lze upravit v mřížce vlastností, ale ostatní vlastnosti je nutné upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] ploše.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Volitelný popisný název aktivity <xref:System.Activities.Statements.CancellationScope>. Výchozí hodnota je CancellationScope. I když hodnota <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Podmínka|Určuje aktivitu, pro kterou je k dispozici logika zrušení. Chcete-li přidat aktivitu <xref:System.Activities.Statements.CancellationScope.Body%2A>, přetáhněte aktivitu ze **sady nástrojů** **do pole text v Návrháři** aktivity **CancellationScope** s textem nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Podmínka|Určuje aktivitu, která se spustí v případě zrušení. Chcete-li přidat aktivitu <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, přetáhněte aktivitu ze **sady nástrojů** do pole **CancellationHandler** v Návrháři aktivity **CancellationScope** s textem nápovědy "Sem přetáhněte aktivitu".|

## <a name="see-also"></a>Viz také
 [](../workflow-designer/transaction-activity-designers.md) [Aktivita CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [](../workflow-designer/compensate-activity-designer.md) transakce s [potvrzením](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)