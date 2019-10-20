---
title: Návrhář aktivity Návrhář postupu provádění – CancellationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a2fd36d81f774ca48cca170b8a4a256d73cf1f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650703"
---
# <a name="cancellationscope-activity-designer"></a>Návrhář aktivity CancellationScope

Návrhář aktivity **CancellationScope** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.CancellationScope>.

## <a name="the-cancellationscope-activity"></a>Aktivita CancellationScope

Aktivita <xref:System.Activities.Statements.CancellationScope> umožňuje určit aktivitu pro provádění a logiku zrušení pro danou aktivitu.

### <a name="using-the-cancellationscope-activity-designer"></a>Pomocí návrháře aktivity CancellationScope

Návrhář aktivity **CancellationScope** lze nalézt v kategorii **transakce** sady **nástrojů**. Chcete-li otevřít **sadu nástrojů**, vyberte kartu **Sada nástrojů** Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** +**ALT** +**X**.

Návrhář aktivity **CancellationScope** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Vyřazením návrháře aktivit **CancellationScope** se vytvoří aktivita <xref:System.Activities.Statements.CancellationScope> s výchozím <xref:System.Activities.Activity.DisplayName%2A> CancellationScope. Upravte hodnotu <xref:System.Activities.Activity.DisplayName%2A> v hlavičce návrháře aktivit **CancellationScope** . Můžete ho také upravit v poli **DisplayName** v mřížce vlastností.

### <a name="the-cancellationscope-properties"></a>Vlastnosti CancellationScope

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.CancellationScope> a popisuje, jak se používají v návrháři. Vlastnost <xref:System.Activities.Activity.DisplayName%2A> lze upravit v mřížce vlastností, ale ostatní vlastnosti je nutné upravovat na Návrhář postupu provádění ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Volitelný popisný název aktivity <xref:System.Activities.Statements.CancellationScope>. Výchozí hodnota je CancellationScope. I když hodnota <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Podmínka|Určuje aktivitu, pro kterou je k dispozici logika zrušení. Chcete-li přidat aktivitu <xref:System.Activities.Statements.CancellationScope.Body%2A>, přetáhněte aktivitu ze **sady nástrojů** do pole **text** v Návrháři aktivity **CancellationScope** . Sem přidejte text nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Podmínka|Určuje aktivitu, která se spustí, pokud dojde ke zrušení. Chcete-li přidat aktivitu <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, přetáhněte aktivitu ze **sady nástrojů** do pole **CancellationHandler** v Návrháři aktivity **CancellationScope** . Sem přidejte text nápovědy "Sem přetáhněte aktivitu".|

## <a name="see-also"></a>Viz také:

- [Transakce](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)