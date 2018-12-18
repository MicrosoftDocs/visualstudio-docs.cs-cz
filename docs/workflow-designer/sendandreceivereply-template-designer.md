---
title: Návrhář postupu provádění – návrhář šablony SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22cdd114a11ff9d1b3b162009cc77d83aec1fd83
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858963"
---
# <a name="sendandreceivereply-template-designer"></a>Návrhář šablony SendAndReceiveReply

**SendAndReceiveReply** šablona se používá k vytvoření páru předem nakonfigurované <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. Aktivity jsou součástí <xref:System.Activities.Statements.Sequence> aktivity a jsou korelována jako součást vzoru výměny zpráv žádost odpověď na straně klienta.

## <a name="the-sendandreceivereply-template"></a>Šablony SendAndReceiveReply

Přidání **SendAndReceiveReply** šablona dělá tři věci kromě vytvoření <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity v rámci <xref:System.Activities.Statements.Sequence> aktivity:

- Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> a <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> vlastnosti <xref:System.ServiceModel.Activities.Send> aktivity.

- Vytvoří vazbu <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> vlastnost <xref:System.ServiceModel.Activities.ReceiveReply> aktivitu <xref:System.ServiceModel.Activities.Send> aktivity.

- Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnná v Nadřazená aktivita.

### <a name="use-the-sendandreceivereply-template-designer"></a>Pomocí nástroje Návrhář šablony SendAndReceiveReply

Přístup **SendAndReceiveReply** návrháře aktivit v **zasílání zpráv** kategorii **nástrojů**. **SendAndReceiveReply** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění bez ohledu na to aktivity jsou obvykle umístěny. Vyřazení Návrhář aktivity vytvoří <xref:System.ServiceModel.Activities.Send> aktivitu, která se dá nakonfigurovat s **odeslat** návrháře aktivit a korelační <xref:System.ServiceModel.Activities.ReceiveReply> , který se dá nakonfigurovat s **ReceiveReplyForSend** návrháře.

Další informace o používání **odeslat** návrháře konfigurace <xref:System.ServiceModel.Activities.Send> aktivity, naleznete v tématu [odeslat](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Vlastnosti ReceiveReply

Následující tabulka ukazuje <xref:System.ServiceModel.Activities.ReceiveReply> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností a můžete upravit některé na povrchu návrháře postupu provádění.


| Název vlastnosti | Požadováno | Použití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Volitelné jméno <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. Výchozí hodnota je ReceiveReplyForSend.<br /><br /> Ačkoli použití jinou než výchozí hodnotu pro popisný <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je vhodné použít taková hodnota. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Hodnota TRUE | Odkaz <xref:System.ServiceModel.Activities.Send> aktivity spárovat s tímto <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. Tato vlastnost nesmí být **null**. <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity se používají společně na straně klienta pro model vzorcem zasílání zpráv žádost odpověď. Tato vlastnost určuje, které <xref:System.ServiceModel.Activities.Send> spárované aktivity. V návrháři, nelze upravit tuto vlastnost, protože je automaticky vázán na <xref:System.ServiceModel.Activities.Send> aktivity, ze kterého jste vytvořili <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Určuje zprávu nebo parametr obsah, který se zobrazí. Může se jednat buď <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivity nebo <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivity. Tato vlastnost upravit kliknutím tlačítko se třemi tečkami vedle možnosti **obsahu** pole v mřížce vlastností nebo kliknutím **definovat** vedle **obsahu** popisek **Receive** povrch návrháře aktivit. Obě zobrazení **definici obsahu** dialogového okna. Další informace o tom, jak pomocí tohoto políčka, naleznete v tématu [obsahu dialogové okno Definice](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objekty, které inicializovat více <xref:System.ServiceModel.Activities.CorrelationHandle> objekty, které to nakonfigurovat <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu. Klikněte na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnost v mřížce vlastnosti otevřít **přidat inicializátory korelace** dialogové okno. Další informace o použití tohoto pole najdete v tématu [dialogové okno Přidat inicializátory korelace](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Určuje akci záhlaví zprávy. Pokud to není explicitně nastavena, její výchozí hodnotu:<br /><br /> <strong>https://tempuri.org/{service obor názvů kontraktu} / {název kontraktu služby} / {název operace}.</strong> |

## <a name="see-also"></a>Viz také:

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)