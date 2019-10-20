---
title: Návrhář aktivity Návrhář postupu provádění – TransactedReceiveScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf5a52a6a806d72632bf31a7c73e41677e9ddaf9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654294"
---
# <a name="transactedreceivescope-activity-designer"></a>Návrhář aktivity TransactedReceiveScope

Návrhář **TransactedReceiveScope** slouží k vytvoření a konfiguraci aktivity <xref:System.ServiceModel.Activities.TransactedReceiveScope>.

## <a name="the-transactedreceivescope-activity"></a>Aktivita TransactedReceiveScope

Aktivita <xref:System.ServiceModel.Activities.TransactedReceiveScope> umožňuje Flow transakci do transakcí serveru vytvořených pomocí pracovního postupu nebo dispečera.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Pomocí návrháře aktivity TransactedReceiveScope

Přístup k Návrháři aktivity **TransactedReceiveScope** v kategorii **zasílání zpráv** sady **nástrojů**. Návrhář aktivity **TransactedReceiveScope** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity. Tím se vytvoří aktivita <xref:System.ServiceModel.Activities.TransactedReceiveScope> s výchozím **názvem DisplayName** TransactedReceiveScope. @No__t_0 lze upravit v hlavičce návrháře aktivity **TransactedReceiveScope** nebo v poli **DisplayName** v mřížce vlastností.

**TransactedReceiveScope** Designer obsahuje pole pro **žádosti** a **text** . Slouží ke konfiguraci vlastnosti <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, která určuje <xref:System.ServiceModel.Activities.Receive> aktivity a vlastnost <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, která určuje další <xref:System.Activities.Activity>. @No__t_0 vytvoří transakci. Transakce se pak rozchází na okolí rozsahu <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> tak, aby se v rámci této transakce provedla jakákoli aktivita v tomto oboru.

### <a name="the-transactedreceivescope-properties"></a>Vlastnosti TransactedReceiveScope

V následující tabulce jsou uvedeny vlastnosti <xref:System.ServiceModel.Activities.TransactedReceiveScope> a popisuje, jak se používají v návrháři. Tyto vlastnosti <xref:System.Activities.Activity.DisplayName%2A> lze upravovat v mřížce vlastností nebo na Návrhář postupu provádění povrchu, ale ostatní musí být upraveny na návrhové ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Volitelný popisný název aktivity <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Výchozí hodnota je TransactedReceiveScope.<br /><br /> I když název <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutný, je osvědčeným postupem použití zobrazovaného názvu.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Podmínka|Zruší aktivitu <xref:System.ServiceModel.Activities.Receive> do bloku **žádosti** na ploše návrháře aktivit.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Zruší <xref:System.Activities.Activity> do bloku **textu** na ploše návrháře aktivit.|

## <a name="see-also"></a>Viz také:

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)