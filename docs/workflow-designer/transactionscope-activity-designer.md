---
title: Návrhář aktivity Návrhář postupu provádění-TransactionScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eef35457b9f28864929ad42919fff4e9afdcb0d5
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114817"
---
# <a name="transactionscope-activity-designer"></a>Návrhář aktivity TransactionScope

Návrhář aktivity **TransactionScope** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.TransactionScope>.

## <a name="the-transactionscope-activity"></a>Aktivita TransactionScope

Aktivita <xref:System.Activities.Statements.TransactionScope> spustí obsaženou aktivitu v jedné transakci. Transakce se potvrdí po úspěšném dokončení aktivity <xref:System.Activities.Statements.TransactionScope.Body%2A> a všech ostatních účastníků v transakci.

### <a name="using-the-transactionscope-activity-designer"></a>Pomocí návrháře aktivit TransactionScope

Přihlaste se k Návrháři aktivit **TransactionScope** v kategorii **transakce** sady **nástrojů**. Návrhář aktivity **TransactionScope** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.TransactionScope> s výchozím <xref:System.Activities.Activity.DisplayName%2A> objektu TransactionScope. Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře aktivit **TransactionScope** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-transactionscope-properties"></a>Vlastnosti objektu TransactionScope

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.TransactionScope> a popisuje, jak se používají v návrháři. Vlastnosti <xref:System.Activities.Activity.DisplayName%2A> a <xref:System.Activities.Statements.TransactionScope.Body%2A> lze upravovat na Návrhář postupu provádění povrchu. Ostatní vlastnosti však musí být upraveny v mřížce vlastností.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Volitelný popisný název aktivity <xref:System.Activities.Statements.TransactionScope>. Výchozím nastavením je objekt TransactionScope. I když hodnota <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Pravda|Určuje aktivitu, která má být spuštěna v rámci jedné transakce. Chcete-li přidat aktivitu <xref:System.Activities.Statements.TransactionScope.Body%2A>, přetáhněte aktivitu ze **sady nástrojů** do pole **text** v Návrháři aktivity **TransactionScope** pomocí textu nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Pravda|Určuje <xref:System.Transactions.IsolationLevel> pro tento <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|Nepravda|Určuje časový interval (formátovaný jako 00:00:00, který označuje hodiny: minuty: sekundy), po kterou musí být transakce dokončena. Výchozí hodnota je 1 minuta (00:01:00).|
|[System. Activities. Statements. TransactionScope. AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|Pravda|Určuje hodnotu, která určuje, zda má být pracovní postup přerušen v případě přerušení transakce.|

## <a name="see-also"></a>Viz také:

- [Transakce](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
