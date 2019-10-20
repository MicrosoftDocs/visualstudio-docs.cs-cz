---
title: Návrhář postupu provádění – Návrhář šablon SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7c552e8bb94ed9035f25bdd40b7944458e61a11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649961"
---
# <a name="sendandreceivereply-template-designer"></a>Návrhář šablony SendAndReceiveReply

Šablona **SendAndReceiveReply** slouží k vytvoření páru předem konfigurovaných aktivit <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply>. Aktivity jsou součástí aktivity <xref:System.Activities.Statements.Sequence> a jsou korelují jako součást vzoru výměny zprávy žádosti nebo odpovědi na klientovi.

## <a name="the-sendandreceivereply-template"></a>Šablona SendAndReceiveReply

Přidání šablony **SendAndReceiveReply** zahrnuje tři věci Kromě vytváření aktivit <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> v rámci <xref:System.Activities.Statements.Sequence> aktivity:

- Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> a <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> vlastnosti aktivity <xref:System.ServiceModel.Activities.Send>.

- Váže vlastnost <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> aktivity <xref:System.ServiceModel.Activities.ReceiveReply> na aktivitu <xref:System.ServiceModel.Activities.Send>.

- Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnnou v nadřazené aktivitě.

### <a name="use-the-sendandreceivereply-template-designer"></a>Použití návrháře šablon SendAndReceiveReply

Přístup k Návrháři aktivity **SendAndReceiveReply** v kategorii **zasílání zpráv** sady **nástrojů**. Návrhář aktivity **SendAndReceiveReply** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity. Vyřazení návrháře aktivit vytvoří aktivitu <xref:System.ServiceModel.Activities.Send>, která se dá nakonfigurovat pomocí návrháře aktivity **odeslání** a korelace <xref:System.ServiceModel.Activities.ReceiveReply>, která se dá nakonfigurovat pomocí návrháře **ReceiveReplyForSend** .

Další informace o použití nástroje **Send** Designer ke konfiguraci aktivity <xref:System.ServiceModel.Activities.Send> naleznete v tématu [Send](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Vlastnosti ReceiveReply

V následující tabulce jsou uvedeny vlastnosti <xref:System.ServiceModel.Activities.ReceiveReply> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé lze upravovat na Návrhář postupu provádění ploše.

| Název vlastnosti | Požadováno | Použití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Volitelný popisný název aktivity <xref:System.ServiceModel.Activities.ReceiveReply>. Výchozí hodnota je ReceiveReplyForSend.<br /><br /> I když použití jiné než výchozí hodnoty pro popisnou <xref:System.Activities.Activity.DisplayName%2A> není naprosto povinné, je vhodné použít takovou hodnotu. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Podmínka | Odkaz na aktivitu <xref:System.ServiceModel.Activities.Send> spárované s touto aktivitou <xref:System.ServiceModel.Activities.ReceiveReply>. Tato vlastnost nesmí mít **hodnotu null**. Aktivity <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> se společně na klientovi používají k modelování vzoru zasílání zpráv požadavku a odpovědí. Tato vlastnost určuje, která aktivita <xref:System.ServiceModel.Activities.Send> se spáruje. V Návrháři tuto vlastnost nelze upravit, protože je automaticky svázána s aktivitou <xref:System.ServiceModel.Activities.Send>, ze které jste vytvořili aktivitu <xref:System.ServiceModel.Activities.ReceiveReply>. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Určuje zprávu nebo parametr obsahu, který se má přijmout. Může to být buď aktivita <xref:System.ServiceModel.Activities.ReceiveMessageContent>, nebo aktivita <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Upravte tuto vlastnost kliknutím na tlačítko se třemi tečkami vedle pole **obsah** v mřížce vlastností nebo kliknutím na tlačítko **definovat** vedle popisku **obsahu** na ploše návrháře aktivity **příjmu** . V obou zobrazeních se zobrazí dialogové okno **definice obsahu** . Další informace o tom, jak používat toto pole, najdete v [dialogovém okně Definice obsahu](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují více objektů <xref:System.ServiceModel.Activities.CorrelationHandle>, které konfigurují tuto <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle vlastnosti <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> v mřížce vlastnosti otevřete dialogové okno **Přidat Inicializátory korelace** . Další informace o použití tohoto pole naleznete v tématu [Add Inicializátoři CorrelationInitializers dialog box](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Určuje hlavičku akce zprávy. Pokud není nastavena explicitně, jeho hodnota se nastaví jako výchozí:<br /><br /> <strong>https://tempuri.org/{service obor názvů kontraktu}/{Service název kontraktu}/{Operation název}.</strong> |

## <a name="see-also"></a>Viz také:

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)