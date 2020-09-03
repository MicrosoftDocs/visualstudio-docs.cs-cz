---
title: Návrhář aktivity Návrhář postupu provádění – CancellationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6d1067b529dffec5a4e6a1f21d5489c32311c07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "76112504"
---
# <a name="cancellationscope-activity-designer"></a>Návrhář aktivity CancellationScope

Návrhář aktivity **CancellationScope** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.CancellationScope> aktivity.

## <a name="the-cancellationscope-activity"></a>Aktivita CancellationScope

<xref:System.Activities.Statements.CancellationScope>Aktivita umožňuje určit aktivitu pro provádění a logiku zrušení pro danou aktivitu.

### <a name="using-the-cancellationscope-activity-designer"></a>Pomocí návrháře aktivity CancellationScope

Návrhář aktivity **CancellationScope** lze nalézt v kategorii **transakce** sady **nástrojů**. Chcete-li otevřít **sadu nástrojů**, vyberte kartu **Sada nástrojů** Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** + **+** + **X**.

Návrhář aktivity **CancellationScope** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Vyřazením návrháře aktivit **CancellationScope** se vytvoří <xref:System.Activities.Statements.CancellationScope> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> CancellationScope. Upravte <xref:System.Activities.Activity.DisplayName%2A> hodnotu v hlavičce návrháře aktivity **CancellationScope** . Můžete ho také upravit v poli **DisplayName** v mřížce vlastností.

### <a name="the-cancellationscope-properties"></a>Vlastnosti CancellationScope

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.CancellationScope> vlastnosti a popisuje, jak se používají v návrháři. <xref:System.Activities.Activity.DisplayName%2A>Vlastnost se dá upravit v mřížce vlastností, ale ostatní vlastnosti se musí upravovat na Návrhář postupu provádění povrchu.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Volitelný popisný název <xref:System.Activities.Statements.CancellationScope> aktivity. Výchozí hodnota je CancellationScope. I když není <xref:System.Activities.Activity.DisplayName%2A> hodnota striktně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Ano|Určuje aktivitu, pro kterou je k dispozici logika zrušení. Chcete-li přidat <xref:System.Activities.Statements.CancellationScope.Body%2A> aktivitu, přetáhněte aktivitu ze **sady nástrojů** do pole **text** v Návrháři aktivity **CancellationScope** . Sem přidejte text nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Ano|Určuje aktivitu, která se spustí, pokud dojde ke zrušení. Chcete-li přidat <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> aktivitu, přetáhněte aktivitu ze **sady nástrojů** do pole **CancellationHandler** v Návrháři aktivity **CancellationScope** . Sem přidejte text nápovědy "Sem přetáhněte aktivitu".|

## <a name="see-also"></a>Viz také

- [Transakce](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
