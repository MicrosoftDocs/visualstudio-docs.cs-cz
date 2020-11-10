---
title: Návrhář aktivity Návrhář postupu provádění – aktivita CompensableActivity
description: Přečtěte si, jak můžete pomocí návrháře aktivit aktivita CompensableActivity vytvořit a nakonfigurovat aktivitu aktivita CompensableActivity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e170bd47af7c84eb9ddb26a4946422c418365d2
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434334"
---
# <a name="compensableactivity-activity-designer"></a>Návrhář aktivity CompensableActivity

Návrhář aktivity **aktivita CompensableActivity** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.CompensableActivity> aktivity.

## <a name="the-compensableactivity-activity"></a>Aktivita aktivita CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity>Definuje jednotku práce, která může být potvrzena nebo nahrazena po úspěšném dokončení.

### <a name="using-the-compensableactivity-activity-designer"></a>Pomocí návrháře aktivity aktivita CompensableActivity
 Návrhář aktivity **aktivita CompensableActivity** lze nalézt v kategorii **transakce** sady **nástrojů**. Chcete-li otevřít **sadu nástrojů** , vyberte kartu **panelu nástrojů** na levé straně Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** + **+** + **X**.

 Návrhář aktivity **aktivita CompensableActivity** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu. Můžete odstranit návrháře aktivit v rámci <xref:System.Activities.Statements.Sequence> . Vyřazení návrháře aktivit vytvoří <xref:System.Activities.Statements.CompensableActivity> aktivitu s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> aktivita CompensableActivity. Upravte <xref:System.Activities.Activity.DisplayName%2A> hodnotu v hlavičce návrháře aktivity **aktivita CompensableActivity** . Můžete ho také upravit v poli **DisplayName** v mřížce vlastností.

### <a name="the-compensableactivity-properties"></a>Vlastnosti aktivita CompensableActivity
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.CompensableActivity> vlastnosti a popisuje, jak se používají v návrháři. <xref:System.Activities.Activity.DisplayName%2A>Vlastnost a <xref:System.Activities.Activity%601.Result%2A> lze upravit v mřížce vlastností, ale ostatní vlastnosti musí být upraveny na Návrhář postupu provádění ploše.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Volitelný popisný název <xref:System.Activities.Statements.CompensableActivity> aktivity. Výchozí hodnota je aktivita CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|Nepravda|Určuje návratovou hodnotu <xref:System.Activities.Statements.CompensableActivity> . Tato vlastnost musí být upravena v mřížce vlastností.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Pravda|Určuje aktivitu, pro kterou je poskytnuta logika kompenzace, zrušení a potvrzení. Chcete-li přidat <xref:System.Activities.Statements.CompensableActivity.Body%2A> aktivitu, přetáhněte aktivitu ze **sady nástrojů** do pole **text** v Návrháři aktivity **aktivita CompensableActivity** . Sem přidejte text nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Nepravda|Určuje aktivitu, která se spustí, když dojde ke zrušení. Chcete-li přidat aktivitu, přetáhněte jejího návrháře ze **sady nástrojů** do pole **CancellationHandler** v Návrháři aktivity **aktivita CompensableActivity** . Přidat text nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Nepravda|Určuje aktivitu, která má být provedena v případě kompenzace <xref:System.Activities.Statements.CompensableActivity.Body%2A> aktivity. Tuto obslužnou rutinu lze explicitně vyvolat pomocí <xref:System.Activities.Statements.Compensate> aktivity.<br /><br /> Chcete-li přidat aktivitu, přetáhněte jejího návrháře aktivit ze **sady nástrojů** do pole **CompensationHandler** v Návrháři aktivity **aktivita CompensableActivity** . Přidat text nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Nepravda|Určuje aktivitu, která má být provedena při potvrzení <xref:System.Activities.Statements.CompensableActivity.Body%2A> aktivity. Tuto obslužnou rutinu lze explicitně vyvolat pomocí <xref:System.Activities.Statements.Confirm> aktivity.<br /><br /> Chcete-li přidat aktivitu, přetáhněte jejího návrháře aktivit ze **sady nástrojů** do pole **ConfirmationHandler** v Návrháři aktivity **aktivita CompensableActivity** . Přidat text nápovědy "Sem přetáhněte aktivitu".|

## <a name="see-also"></a>Viz také

- [Transakce](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
