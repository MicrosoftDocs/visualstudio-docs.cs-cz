---
title: Návrhář aktivity Návrhář postupu provádění – aktivita CompensableActivity
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
ms.openlocfilehash: 7ec70c22ae195dc6dd58aa2cfa893cee35fe6ca8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597097"
---
# <a name="compensableactivity-activity-designer"></a>Návrhář aktivity CompensableActivity

Návrhář aktivity **aktivita CompensableActivity** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.CompensableActivity>.

## <a name="the-compensableactivity-activity"></a>Aktivita aktivita CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> definuje jednotku práce, kterou lze potvrdit nebo kompenzovat po úspěšném dokončení.

### <a name="using-the-compensableactivity-activity-designer"></a>Pomocí návrháře aktivity aktivita CompensableActivity
 Návrhář aktivity **aktivita CompensableActivity** lze nalézt v kategorii **transakce** sady **nástrojů**. Chcete-li otevřít **sadu nástrojů**, vyberte kartu **panelu nástrojů** na levé straně Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL**+**ALT**+**X**.

 Návrhář aktivity **aktivita CompensableActivity** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu. Můžete vyřadit návrháře aktivit v rámci <xref:System.Activities.Statements.Sequence>. Vyřazení návrháře aktivit vytvoří aktivitu <xref:System.Activities.Statements.CompensableActivity> s výchozím <xref:System.Activities.Activity.DisplayName%2A> aktivita CompensableActivity. Upravte hodnotu <xref:System.Activities.Activity.DisplayName%2A> v hlavičce návrháře aktivit **aktivita CompensableActivity** . Můžete ho také upravit v poli **DisplayName** v mřížce vlastností.

### <a name="the-compensableactivity-properties"></a>Vlastnosti aktivita CompensableActivity
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.CompensableActivity> a popisuje, jak se používají v návrháři. Vlastnost <xref:System.Activities.Activity.DisplayName%2A> a <xref:System.Activities.Activity%601.Result%2A> lze upravovat v mřížce vlastností, ale ostatní vlastnosti je nutné upravovat na Návrhář postupu provádění ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Volitelný popisný název aktivity <xref:System.Activities.Statements.CompensableActivity>. Výchozí hodnota je aktivita CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|Nepravda|Určuje návratovou hodnotu <xref:System.Activities.Statements.CompensableActivity>. Tato vlastnost musí být upravena v mřížce vlastností.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Pravda|Určuje aktivitu, pro kterou je poskytnuta logika kompenzace, zrušení a potvrzení. Chcete-li přidat aktivitu <xref:System.Activities.Statements.CompensableActivity.Body%2A>, přetáhněte aktivitu ze **sady nástrojů** do pole **text** v Návrháři aktivity **aktivita CompensableActivity** . Sem přidejte text nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Nepravda|Určuje aktivitu, která se spustí, když dojde ke zrušení. Chcete-li přidat aktivitu, přetáhněte jejího návrháře ze **sady nástrojů** do pole **CancellationHandler** v Návrháři aktivity **aktivita CompensableActivity** . Přidat text nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Nepravda|Určuje aktivitu, která má být provedena při odškodnění aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Tuto obslužnou rutinu lze explicitně vyvolat pomocí aktivity <xref:System.Activities.Statements.Compensate>.<br /><br /> Chcete-li přidat aktivitu, přetáhněte jejího návrháře aktivit ze **sady nástrojů** do pole **CompensationHandler** v Návrháři aktivity **aktivita CompensableActivity** . Přidat text nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Nepravda|Určuje aktivitu, která má být provedena při potvrzení aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Tuto obslužnou rutinu lze explicitně vyvolat pomocí aktivity <xref:System.Activities.Statements.Confirm>.<br /><br /> Chcete-li přidat aktivitu, přetáhněte jejího návrháře aktivit ze **sady nástrojů** do pole **ConfirmationHandler** v Návrháři aktivity **aktivita CompensableActivity** . Přidat text nápovědy "Sem přetáhněte aktivitu".|

## <a name="see-also"></a>Viz také:

- [Transakce](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
