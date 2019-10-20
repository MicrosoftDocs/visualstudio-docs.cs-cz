---
title: Návrhář aktivity TransactionScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5a1d38ea37896cedcd2166c42f37ce037a1c4cd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670177"
---
# <a name="transactionscope-activity-designer"></a>Návrhář aktivity TransactionScope
Návrhář aktivity **TransactionScope** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.TransactionScope>.

## <a name="the-transactionscope-activity"></a>Aktivita TransactionScope
 Aktivita <xref:System.Activities.Statements.TransactionScope> spustí obsaženou aktivitu v jedné transakci. Transakce se potvrdí po úspěšném dokončení aktivity <xref:System.Activities.Statements.TransactionScope.Body%2A> a všech ostatních účastníků v transakci.

### <a name="using-the-transactionscope-activity-designer"></a>Pomocí návrháře aktivit TransactionScope
 Návrhář aktivity **TransactionScope** se dá najít v kategorii **transakce** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** ze **zobrazení).** v nabídce nebo CTRL + ALT + X.)

 Návrhář aktivity **TransactionScope** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.TransactionScope> s výchozím <xref:System.Activities.Activity.DisplayName%2A> objektu TransactionScope. Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře aktivit **TransactionScope** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-transactionscope-properties"></a>Vlastnosti objektu TransactionScope
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.TransactionScope> a popisuje, jak se používají v návrháři. Vlastnosti <xref:System.Activities.Activity.DisplayName%2A> a <xref:System.Activities.Statements.TransactionScope.Body%2A> lze upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu. Ostatní vlastnosti však musí být upraveny v mřížce vlastností.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Volitelný popisný název aktivity <xref:System.Activities.Statements.TransactionScope>. Výchozím nastavením je objekt TransactionScope. I když hodnota <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Podmínka|Určuje aktivitu, která má být spuštěna v rámci jedné transakce. Chcete-li přidat aktivitu <xref:System.Activities.Statements.TransactionScope.Body%2A>, přetáhněte aktivitu ze **sady nástrojů** do pole **text** v Návrháři aktivity **TransactionScope** pomocí textu nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Podmínka|Určuje <xref:System.Transactions.IsolationLevel> pro tento <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Určuje časový interval (formátovaný jako 00:00:00, který označuje hodiny: minuty: sekundy), po kterou musí být transakce dokončena. Výchozí hodnota je 1 minuta (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|Podmínka|Určuje hodnotu, která určuje, zda má být pracovní postup přerušen v případě přerušení transakce.|

## <a name="see-also"></a>Viz také
 [Potvrzení](../workflow-designer/confirm-activity-designer.md) [kompenzace](../workflow-designer/compensate-activity-designer.md) [aktivita CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [transakce](../workflow-designer/transaction-activity-designers.md) [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)