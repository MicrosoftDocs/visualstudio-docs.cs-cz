---
title: Návrhář šablony ReceiveAndSendReply
description: Naučte se, jak pomocí šablony ReceiveAndSendReply v Návrhář postupu provádění vytvořit dvojici předem nakonfigurovaných aktivit Receive a SendReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f11caa831ca3de0684dd49e46a37620eaa6e435
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996211"
---
# <a name="receiveandsendreply-template-designer"></a>Návrhář šablony ReceiveAndSendReply

Šablona **ReceiveAndSendReply** slouží k vytvoření dvojice předem nakonfigurovaných <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> aktivit a. Aktivity jsou součástí <xref:System.Activities.Statements.Sequence> aktivity a jsou korelační jako součást vzoru výměny zpráv požadavků a odpovědí na serveru.

## <a name="the-receiveandsendreply-template"></a>Šablona ReceiveAndSendReply

Přidání šablony **ReceiveAndSendReply** zahrnuje tři věci Kromě vytváření <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> aktivit a aktivity s <xref:System.Activities.Statements.Sequence> aktivitou:

- Nakonfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> vlastnosti a <xref:System.ServiceModel.Activities.Receive> aktivity.

- Váže <xref:System.ServiceModel.Activities.SendReply.Request%2A> vlastnost <xref:System.ServiceModel.Activities.Receive> aktivity na <xref:System.ServiceModel.Activities.Send> aktivitu.

- Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnnou v nadřazené aktivitě.

### <a name="use-the-receiveandsendreply-template-designer"></a>Použití návrháře šablon ReceiveAndSendReply

Přístup k Návrháři aktivity **ReceiveAndSendReply** v kategorii **zasílání zpráv** sady **nástrojů**. Návrhář aktivity **ReceiveAndSendReply** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity. Vyřazení návrháře aktivit vytvoří <xref:System.ServiceModel.Activities.Receive> aktivitu, která se dá nakonfigurovat pomocí návrháře aktivity **odeslání** a korelace <xref:System.ServiceModel.Activities.SendReply> , která se dá nakonfigurovat pomocí návrháře SendReplyToReceive.

Další informace o konfiguraci aktivity pomocí návrháře **příjmu** <xref:System.ServiceModel.Activities.Receive> najdete v tématu věnovaném [nástroji Receive Activity Designer](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Vlastnosti pro aktivitu SendReply

V následující tabulce jsou uvedeny <xref:System.ServiceModel.Activities.SendReply> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé lze upravovat na Návrhář postupu provádění ploše.

| Název vlastnosti | Požaduje se | Využití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Ne | Volitelný popisný název <xref:System.ServiceModel.Activities.SendReply> aktivity. Výchozí hodnota je SendReplyToReceive.<br /><br /> I když použití jiné než výchozí hodnoty pro popis není <xref:System.Activities.Activity.DisplayName%2A> naprosto povinné, je vhodné použít takovou hodnotu. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | Ano | Odkaz na <xref:System.ServiceModel.Activities.Receive> aktivitu spárované s touto <xref:System.ServiceModel.Activities.SendReply> aktivitou Tato vlastnost nesmí mít **hodnotu null**. <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity se společně na serveru používají k modelování vzoru zasílání zpráv požadavku a odpovědí. Tato vlastnost určuje, která <xref:System.ServiceModel.Activities.Send> aktivita se spáruje. V Návrháři tuto vlastnost nemůžete upravit, protože je automaticky svázána s <xref:System.ServiceModel.Activities.Send> aktivitou, ze které jste <xref:System.ServiceModel.Activities.SendReply> aktivitu vytvořili. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | Ne | Určuje zprávu nebo parametr obsahu, který se má přijmout. Může to být buď <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivita, nebo <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivita. Tuto vlastnost můžete upravit kliknutím na tlačítko se třemi tečkami vedle pole **obsah** v mřížce vlastností nebo kliknutím na tlačítko **definovat** vedle popisku **obsahu** na ploše návrháře aktivity **příjmu** . V obou zobrazeních se zobrazí dialogové okno **definice obsahu** . Další informace o tom, jak používat toto pole, najdete v tématu věnovaném [definici obsahu v dialogu](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | Ne | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují více <xref:System.ServiceModel.Activities.CorrelationHandle> objektů, které konfigurují tuto <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> vlastnosti v mřížce vlastnosti otevřete dialogové okno **Přidat Inicializátory korelace** . Další informace o použití tohoto pole najdete v tématu věnovaném [dialogovému oknu Přidat inicializátoři CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | Ne | Určuje hlavičku akce zprávy. Pokud není nastavena explicitně, jeho hodnota se nastaví jako výchozí:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | Ne | Určuje, zda má být instance pracovního postupu trvalá před odesláním zprávy s odpovědí. Výchozí hodnota je **false** (nepravda). |

## <a name="see-also"></a>Viz také

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Přijmout](../workflow-designer/receive-activity-designer.md)
- [Odeslat](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)