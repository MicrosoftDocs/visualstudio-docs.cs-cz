---
title: Návrhář aktivity aktivita CompensableActivity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2bc28c4586912d7c253c9629c2af0eefd30e47e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656997"
---
# <a name="compensableactivity-activity-designer"></a>Návrhář aktivity CompensableActivity
Návrhář aktivity **aktivita CompensableActivity** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.CompensableActivity>.

## <a name="the-compensableactivity-activity"></a>Aktivita aktivita CompensableActivity
 @No__t_0 definuje jednotku práce, kterou lze potvrdit nebo kompenzovat po úspěšném dokončení.

### <a name="using-the-compensableactivity-activity-designer"></a>Pomocí návrháře aktivity aktivita CompensableActivity
 Návrhář aktivity **aktivita CompensableActivity** se dá najít v kategorii **transakce** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte **panel nástrojů** . v nabídce **zobrazení** nebo CTRL + ALT + X.)

 Návrhář aktivity **aktivita CompensableActivity** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.CompensableActivity> s výchozím <xref:System.Activities.Activity.DisplayName%2A> aktivita CompensableActivity. Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře aktivity **aktivita CompensableActivity** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-compensableactivity-properties"></a>Vlastnosti aktivita CompensableActivity
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.CompensableActivity> a popisuje, jak se používají v návrháři. Vlastnost <xref:System.Activities.Activity.DisplayName%2A> a <xref:System.Activities.Activity%601.Result%2A> lze upravovat v mřížce vlastností, ale ostatní vlastnosti je nutné upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] ploše.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Volitelný popisný název aktivity <xref:System.Activities.Statements.CompensableActivity>. Výchozí hodnota je aktivita CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Určuje návratovou hodnotu <xref:System.Activities.Statements.CompensableActivity>. Tato vlastnost musí být upravena v mřížce vlastností.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Podmínka|Určuje aktivitu, pro kterou je poskytnuta logika kompenzace, zrušení a potvrzení. Chcete-li přidat aktivitu <xref:System.Activities.Statements.CompensableActivity.Body%2A>, přetáhněte aktivitu ze **sady nástrojů** **do pole text v Návrháři** aktivity **aktivita CompensableActivity** s textem nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Určuje aktivitu, která se spustí v případě zrušení. Chcete-li přidat aktivitu, přetáhněte jejího návrháře z **panelu nástrojů** do pole **CancellationHandler** v Návrháři aktivity **aktivita CompensableActivity** s textem nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Určuje aktivitu, která má být provedena při odškodnění aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Tuto obslužnou rutinu lze explicitně vyvolat pomocí aktivity <xref:System.Activities.Statements.Compensate>.<br /><br /> Chcete-li přidat aktivitu, přetáhněte její Návrhář aktivity z **panelu nástrojů** do pole **CompensationHandler** v Návrháři aktivity **aktivita CompensableActivity** s textem nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Určuje aktivitu, která má být provedena při potvrzení aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Tuto obslužnou rutinu lze explicitně vyvolat pomocí aktivity <xref:System.Activities.Statements.Confirm>.<br /><br /> Chcete-li přidat aktivitu, přetáhněte její Návrhář aktivity z **panelu nástrojů** do pole **ConfirmationHandler** v Návrháři aktivity **aktivita CompensableActivity** s textem nápovědy "Sem přetáhněte aktivitu".|

## <a name="see-also"></a>Viz také
 [](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [](../workflow-designer/compensate-activity-designer.md) transakce s [potvrzením](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)