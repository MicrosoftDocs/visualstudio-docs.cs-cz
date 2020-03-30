---
title: Návrhář pracovního postupu - Návrhář šablony SendAndReceiveReply
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
ms.openlocfilehash: 2067ee92883d0c4ad3003f23032a88f5da3fa710
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395249"
---
# <a name="sendandreceivereply-template-designer"></a>Návrhář šablony SendAndReceiveReply

Šablona **SendAndReceiveReply** se používá k vytvoření <xref:System.ServiceModel.Activities.Send> dvojice <xref:System.ServiceModel.Activities.ReceiveReply> předem nakonfigurovaných a aktivit. Aktivity jsou součástí <xref:System.Activities.Statements.Sequence> aktivity a jsou korelovány jako součást vzoru výměny zpráv požadavek/odpověď na straně klienta.

## <a name="the-sendandreceivereply-template"></a>Šablona SendAndReceiveReply

Přidání **SendAndReceiveReply** šablony provádí tři <xref:System.ServiceModel.Activities.Send> věci <xref:System.ServiceModel.Activities.ReceiveReply> kromě <xref:System.Activities.Statements.Sequence> vytváření a aktivity v rámci aktivity:

- Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> vlastnosti <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> a aktivity. <xref:System.ServiceModel.Activities.Send>

- Sváže <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> vlastnost aktivity <xref:System.ServiceModel.Activities.ReceiveReply> s <xref:System.ServiceModel.Activities.Send> aktivitou.

- Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnnou v nadřazené aktivitě.

### <a name="use-the-sendandreceivereply-template-designer"></a>Použití návrháře šablon SendAndReceiveReply

Přístup k návrháři aktivit **SendAndReceiveReply** v kategorii **Zasílání zpráv** v **panelu nástrojů**. Návrháře aktivit **SendAndReceiveReply** lze přetáhnout z **panelu nástrojů** a přetáhnout na povrch návrháře pracovních postupů, kde jsou obvykle umístěny aktivity. Uvolněním návrháře <xref:System.ServiceModel.Activities.Send> aktivit vytvoří aktivitu, která může být <xref:System.ServiceModel.Activities.ReceiveReply> nakonfigurována pomocí návrháře aktivit **odesílání** a korelační, který lze nakonfigurovat pomocí návrháře **ReceiveReplyForSend.**

Další informace o konfiguraci aktivity <xref:System.ServiceModel.Activities.Send> pomocí návrháře **odeslat** naleznete v tématu [Odeslání](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Vlastnosti receivereply

V následující tabulce <xref:System.ServiceModel.Activities.ReceiveReply> jsou uvedeny vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností a některé lze upravovat na povrchu Návrháře pracovních postupů.

| Název vlastnosti | Požaduje se | Využití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Volitelný popisný název <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. Výchozí hodnota je ReceiveReplyForSend.<br /><br /> Přestože použití hodnoty, která není <xref:System.Activities.Activity.DisplayName%2A> výchozí pro přátelské, není nezbytně nutné, je nejlepší použít takovou hodnotu. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Odkaz na <xref:System.ServiceModel.Activities.Send> aktivitu <xref:System.ServiceModel.Activities.ReceiveReply> spárovanou s touto aktivitou. Tato vlastnost nesmí mít **hodnotu null**. <xref:System.ServiceModel.Activities.Send>a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity se používají společně na straně klienta k modelování vzoru zasílání zpráv požadavku a odpovědi. Tato vlastnost určuje, která <xref:System.ServiceModel.Activities.Send> aktivita je spárována. V návrháři nelze tuto vlastnost upravit, protože je automaticky <xref:System.ServiceModel.Activities.Send> vázána na <xref:System.ServiceModel.Activities.ReceiveReply> aktivitu, ze které jste aktivitu vytvořili. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Určuje zprávu nebo obsah parametrů, který má být přijímán. Může to být <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivita <xref:System.ServiceModel.Activities.ReceiveParametersContent> nebo aktivita. Upravte tuto vlastnost kliknutím na tlačítko se třemi tečkami vedle pole **Obsah** v mřížce vlastností nebo kliknutím na tlačítko **Definovat** vedle popisku **Obsah** na povrchu návrháře **aktivit příjmu.** Obě zobrazí dialogové **okno Definice obsahu.** Další informace o použití tohoto pole naleznete v [dialogovém okně Definice obsahu](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Receive> více objektů, které konfigurují tuto aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnosti v mřížce vlastností otevřete dialogové okno Přidat **intezivace korelace.** Další informace o použití tohoto pole naleznete v [tématu Přidání dialogového okna Korelace initializérů](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Určuje záhlaví akce zprávy. Pokud není explicitně nastavena, jeho hodnota je výchozí:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Viz také

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Přijmout](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Odeslat](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)