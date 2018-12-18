---
title: Návrhář postupu provádění – Návrhář aktivity CompensableActivity
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7257e7cc31e0503c7e466bbf4f8c9dd02e5fe15a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836125"
---
# <a name="compensableactivity-activity-designer"></a>Návrhář aktivity CompensableActivity

**Aktivita CompensableActivity** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.Activities.Statements.CompensableActivity> aktivity.

## <a name="the-compensableactivity-activity"></a>Aktivita CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> Definuje jednotku práce, které mohou být potvrzena nebo kompenzována po úspěšném dokončení.

### <a name="using-the-compensableactivity-activity-designer"></a>Návrhář aktivity CompensableActivity pomocí
 **Aktivita CompensableActivity** návrháře aktivit najdete v **transakce** kategorie **nástrojů**. Chcete-li otevřít **nástrojů**, vyberte **nástrojů** karty na levé straně návrháře postupu provádění. Můžete také vybrat **nástrojů** z **zobrazení** nabídky nebo stisknutím klávesy **Ctrl**+**Alt** + **X**.

 **Aktivita CompensableActivity** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění. Může vyřadit návrháře aktivit uvnitř <xref:System.Activities.Statements.Sequence>. Vyřazení Návrhář aktivity vytvoří <xref:System.Activities.Statements.CompensableActivity> aktivity s výchozím <xref:System.Activities.Activity.DisplayName%2A> z aktivita CompensableActivity. Upravit <xref:System.Activities.Activity.DisplayName%2A> hodnota v hlavičce **aktivita CompensableActivity** návrháře aktivit. Můžete upravit také v **DisplayName** pole mřížku vlastností.

### <a name="the-compensableactivity-properties"></a>Aktivita CompensableActivity vlastnosti
 Následující tabulka ukazuje <xref:System.Activities.Statements.CompensableActivity> vlastnosti a popisuje, jak se používají v návrháři. <xref:System.Activities.Activity.DisplayName%2A> a <xref:System.Activities.Activity%601.Result%2A> vlastnost lze upravit v mřížce vlastností, ale další vlastnosti nutné upravit na povrchu návrháře postupu provádění.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Volitelné jméno <xref:System.Activities.Statements.CompensableActivity> aktivity. Výchozí hodnota je aktivita CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Určuje návratovou hodnotu <xref:System.Activities.Statements.CompensableActivity>. Tato vlastnost je nutné upravit v mřížce vlastností.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Hodnota TRUE|Určuje aktivity, pro který je k dispozici logiky compensation, zrušení a potvrzení. Přidat <xref:System.Activities.Statements.CompensableActivity.Body%2A> aktivity, rozevírací aktivitu z **nástrojů** do **tělo** pole na **aktivita CompensableActivity** návrháře aktivit. Přidáte text nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Určuje, který se spouští při zrušení aktivity. Přidat aktivitu, vyřaďte Návrhář z **nástrojů** do **CancellationHandler** pole na **aktivita CompensableActivity** návrháře aktivit. Přidáte text nápovědy "Aktivity Sem přetáhněte".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Určuje aktivity, který se spustí při kompenzaci pro <xref:System.Activities.Statements.CompensableActivity.Body%2A> aktivity. Tato obslužná rutina může být vyvolána explicitně, pomocí <xref:System.Activities.Statements.Compensate> aktivity.<br /><br /> Přidat aktivitu, přetáhněte jeho Návrhář aktivity z **nástrojů** do **CompensationHandler** pole na **aktivita CompensableActivity** návrháře aktivit. Přidáte text nápovědy "Aktivity Sem přetáhněte".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Určuje aktivity, který se spustí při potvrzení <xref:System.Activities.Statements.CompensableActivity.Body%2A> aktivity. Tato obslužná rutina může být vyvolána explicitně, pomocí <xref:System.Activities.Statements.Confirm> aktivity.<br /><br /> Přidat aktivitu, přetáhněte jeho Návrhář aktivity z **nástrojů** do **ConfirmationHandler** pole na **aktivita CompensableActivity** návrháře aktivit. Přidáte text nápovědy "Aktivity Sem přetáhněte".|

## <a name="see-also"></a>Viz také:

- [Transakce](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)