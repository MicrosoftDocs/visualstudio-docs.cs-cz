---
title: Návrhář postupu provádění – Návrhář šablon SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17512337b58fb394352ccaab153ca72badbb4652
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875901"
---
# <a name="sendandreceivereply-template-designer"></a>Návrhář šablony SendAndReceiveReply

Šablona **SendAndReceiveReply** slouží k vytvoření dvojice předem nakonfigurovaných <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> aktivit a. Aktivity jsou součástí <xref:System.Activities.Statements.Sequence> aktivity a jsou korelují jako součást vzoru výměny zprávy žádosti nebo odpovědi na klientovi.

## <a name="the-sendandreceivereply-template"></a>Šablona SendAndReceiveReply

Přidání šablony **SendAndReceiveReply** zahrnuje tři věci Kromě vytváření <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> aktivit a v rámci <xref:System.Activities.Statements.Sequence> aktivity:

- Nakonfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> vlastnosti a <xref:System.ServiceModel.Activities.Send> aktivity.

- Váže <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> vlastnost <xref:System.ServiceModel.Activities.ReceiveReply> aktivity na <xref:System.ServiceModel.Activities.Send> aktivitu.

- Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnnou v nadřazené aktivitě.

### <a name="use-the-sendandreceivereply-template-designer"></a>Použití návrháře šablon SendAndReceiveReply

Přístup k Návrháři aktivity **SendAndReceiveReply** v kategorii **zasílání zpráv** sady **nástrojů**. Návrhář aktivity **SendAndReceiveReply** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity. Vyřazení návrháře aktivit vytvoří <xref:System.ServiceModel.Activities.Send> aktivitu, která se dá nakonfigurovat pomocí návrháře aktivity **odeslání** a korelace <xref:System.ServiceModel.Activities.ReceiveReply> , která se dá nakonfigurovat pomocí návrháře **ReceiveReplyForSend** .

Další informace o konfiguraci aktivity pomocí návrháře **odeslání** <xref:System.ServiceModel.Activities.Send> najdete v tématu [odeslání](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Vlastnosti ReceiveReply

V následující tabulce jsou uvedeny <xref:System.ServiceModel.Activities.ReceiveReply> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé lze upravovat na Návrhář postupu provádění ploše.

| Název vlastnosti | Požaduje se | Využití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Ne | Volitelný popisný název <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. Výchozí hodnota je ReceiveReplyForSend.<br /><br /> I když použití jiné než výchozí hodnoty pro popis není <xref:System.Activities.Activity.DisplayName%2A> naprosto povinné, je vhodné použít takovou hodnotu. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Ano | Odkaz na <xref:System.ServiceModel.Activities.Send> aktivitu spárované s touto <xref:System.ServiceModel.Activities.ReceiveReply> aktivitou Tato vlastnost nesmí mít **hodnotu null**. <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity se v klientovi používají k modelování vzoru zasílání zpráv požadavek/odpověď. Tato vlastnost určuje, která <xref:System.ServiceModel.Activities.Send> aktivita se spáruje. V Návrháři tuto vlastnost nemůžete upravit, protože je automaticky svázána s <xref:System.ServiceModel.Activities.Send> aktivitou, ze které jste <xref:System.ServiceModel.Activities.ReceiveReply> aktivitu vytvořili. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | Ne | Určuje zprávu nebo parametr obsahu, který se má přijmout. Může to být buď <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivita, nebo <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivita. Upravte tuto vlastnost kliknutím na tlačítko se třemi tečkami vedle pole **obsah** v mřížce vlastností nebo kliknutím na tlačítko **definovat** vedle popisku **obsahu** na ploše návrháře aktivity **příjmu** . V obou zobrazeních se zobrazí dialogové okno **definice obsahu** . Další informace o tom, jak používat toto pole, najdete v [dialogovém okně Definice obsahu](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | Ne | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují více <xref:System.ServiceModel.Activities.CorrelationHandle> objektů, které konfigurují tuto <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnosti v mřížce vlastnosti otevřete dialogové okno **Přidat Inicializátory korelace** . Další informace o použití tohoto pole naleznete v tématu [Add Inicializátoři CorrelationInitializers dialog box](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | Ne | Určuje hlavičku akce zprávy. Pokud není nastavena explicitně, jeho hodnota se nastaví jako výchozí:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Viz také

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Přijmout](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Odeslat](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)