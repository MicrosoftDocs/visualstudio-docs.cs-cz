---
title: Návrhář pracovního postupu – Návrhář šablony ReceiveAndSendReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 042032efe745a9cb38bbf4e362cb5ad8440129ba
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395303"
---
# <a name="receiveandsendreply-template-designer"></a>Návrhář šablony ReceiveAndSendReply

Šablona **ReceiveAndSendReply** se používá k vytvoření <xref:System.ServiceModel.Activities.Receive> dvojice <xref:System.ServiceModel.Activities.SendReply> předem nakonfigurovaných a aktivit. Aktivity jsou součástí <xref:System.Activities.Statements.Sequence> aktivity a jsou korelovány jako součást vzoru výměny zpráv požadavek/odpověď na serveru.

## <a name="the-receiveandsendreply-template"></a>Šablona ReceiveAndSendReply

Přidání **receiveAndSendReply** šablony provádí tři <xref:System.ServiceModel.Activities.Receive> věci <xref:System.ServiceModel.Activities.SendReply> kromě <xref:System.Activities.Statements.Sequence> vytváření a aktivity s aktivitou:

- Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A> vlastnosti <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> a aktivity. <xref:System.ServiceModel.Activities.Receive>

- Sváže <xref:System.ServiceModel.Activities.SendReply.Request%2A> vlastnost aktivity <xref:System.ServiceModel.Activities.Receive> s <xref:System.ServiceModel.Activities.Send> aktivitou.

- Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnnou v nadřazené aktivitě.

### <a name="use-the-receiveandsendreply-template-designer"></a>Použití návrháře šablon ReceiveAndSendReply

Přístup k návrháři aktivit **ReceiveAndSendReply** v kategorii **Zasílání zpráv** v **panelu nástrojů**. Návrháře aktivit **ReceiveAndSendReply** lze přetáhnout z **panelu nástrojů** a přetáhnout na povrch návrháře pracovních postupů, kde jsou obvykle umístěny aktivity. Uvolněním návrháře <xref:System.ServiceModel.Activities.Receive> aktivit vytvoří aktivitu, která může být <xref:System.ServiceModel.Activities.SendReply> nakonfigurována s návrhářem aktivit **odesílání** a korelační, který lze nakonfigurovat s návrhářem SendReplyToReceive.

Další informace o **Receive** použití návrháře <xref:System.ServiceModel.Activities.Receive> příjmu ke konfiguraci aktivity naleznete v tématu [Příjem Návrháře aktivit](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Vlastnosti SendReply

V následující tabulce <xref:System.ServiceModel.Activities.SendReply> jsou uvedeny vlastnosti a popisuje, jak jsou používány v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností a některé lze upravovat na povrchu Návrháře pracovních postupů.

| Název vlastnosti | Požaduje se | Využití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Volitelný popisný název <xref:System.ServiceModel.Activities.SendReply> aktivity. Výchozí hodnota je SendReplyToReceive.<br /><br /> Přestože použití hodnoty, která není <xref:System.Activities.Activity.DisplayName%2A> výchozí pro přátelské, není nezbytně nutné, je nejlepší použít takovou hodnotu. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Odkaz na <xref:System.ServiceModel.Activities.Receive> aktivitu <xref:System.ServiceModel.Activities.SendReply> spárovanou s touto aktivitou. Tato vlastnost nesmí mít **hodnotu null**. <xref:System.ServiceModel.Activities.Receive>a <xref:System.ServiceModel.Activities.SendReply> aktivity se používají společně na serveru k modelování vzoru zasílání zpráv požadavku a odpovědi. Tato vlastnost určuje, která <xref:System.ServiceModel.Activities.Send> aktivita je spárována. V návrháři nelze tuto vlastnost upravit, protože je automaticky <xref:System.ServiceModel.Activities.Send> vázána na <xref:System.ServiceModel.Activities.SendReply> aktivitu, ze které jste aktivitu vytvořili. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Určuje zprávu nebo obsah parametrů, který má být přijímán. Může to být <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivita <xref:System.ServiceModel.Activities.ReceiveParametersContent> nebo aktivita. Upravte tuto vlastnost kliknutím na tlačítko se třemi tečkami vedle pole **Obsah** v mřížce vlastností nebo kliknutím na tlačítko **Definovat** vedle popisku **Obsah** na povrchu návrháře **aktivit příjmu.** Obě zobrazí dialogové **okno Definice obsahu.** Další informace o použití tohoto pole naleznete v tématu [dialogového okna Definice obsahu.](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Receive> více objektů, které konfigurují tuto aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> vlastnosti v mřížce vlastností otevřete dialogové okno Přidat **intezivace korelace.** Další informace o použití tohoto pole naleznete v tématu [dialogového okna Přidat korelaciinivázivalizé inkrese.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Určuje záhlaví akce zprávy. Pokud není explicitně nastavena, jeho hodnota je výchozí:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Určuje, zda má být instance pracovního postupu před odesláním zprávy s odpovědí zachována. Výchozí hodnota je **false** (nepravda). |

## <a name="see-also"></a>Viz také

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Přijmout](../workflow-designer/receive-activity-designer.md)
- [Odeslat](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)