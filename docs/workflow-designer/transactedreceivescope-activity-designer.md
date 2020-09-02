---
title: Návrhář aktivity Návrhář postupu provádění – TransactedReceiveScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75fb1da392bce7dbd0cd7849d83b3b452521e0c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875927"
---
# <a name="transactedreceivescope-activity-designer"></a>Návrhář aktivity TransactedReceiveScope

Návrhář **TransactedReceiveScope** slouží k vytvoření a konfiguraci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.

## <a name="the-transactedreceivescope-activity"></a>Aktivita TransactedReceiveScope

<xref:System.ServiceModel.Activities.TransactedReceiveScope>Aktivita umožňuje Flow transakci do transakcí serveru vytvořených pomocí pracovního postupu nebo dispečera.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Pomocí návrháře aktivity TransactedReceiveScope

Přístup k Návrháři aktivity **TransactedReceiveScope** v kategorii **zasílání zpráv** sady **nástrojů**. Návrhář aktivity **TransactedReceiveScope** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity. Tím se vytvoří <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivita s výchozím **názvem DisplayName** TransactedReceiveScope. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře aktivity **TransactedReceiveScope** nebo v poli **DisplayName** v mřížce vlastností.

**TransactedReceiveScope** Designer obsahuje pole pro **žádosti** a **text** . Slouží ke konfiguraci <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> vlastnosti, která určuje <xref:System.ServiceModel.Activities.Receive> aktivitu a <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> vlastnost, která určuje jiné <xref:System.Activities.Activity> . <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>Vytvoří transakci. Transakce pak bude provedeno okolí pro rozsah, aby byla v <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> rámci této transakce provedena jakákoli aktivita v tomto oboru.

### <a name="the-transactedreceivescope-properties"></a>Vlastnosti TransactedReceiveScope

V následující tabulce jsou uvedeny <xref:System.ServiceModel.Activities.TransactedReceiveScope> vlastnosti a popisuje, jak se používají v návrháři. Tato <xref:System.Activities.Activity.DisplayName%2A> vlastnost se dá upravovat v mřížce vlastností nebo na Návrhář postupu provádění povrchu, ale ostatní se musí upravovat na návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Volitelný popisný název <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity. Výchozí hodnota je TransactedReceiveScope.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> název není nezbytně nutný, je osvědčeným postupem použití zobrazovaného názvu.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Ano|Zruší <xref:System.ServiceModel.Activities.Receive> aktivitu do bloku **žádosti** na povrchu návrháře aktivit.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Ne|Přenechá <xref:System.Activities.Activity> do bloku **text** na ploše návrháře aktivit.|

## <a name="see-also"></a>Viz také

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Přijmout](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Odeslat](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)