---
title: Návrhář postupu provádění – návrhář šablony ReceiveAndSendReply
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c6b5a12b37509e6e5113c704ef2c3ff931ea32e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886406"
---
# <a name="receiveandsendreply-template-designer"></a>Návrhář šablony ReceiveAndSendReply

**ReceiveAndSendReply** šablona se používá k vytvoření páru předem nakonfigurované <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity. Aktivity jsou součástí <xref:System.Activities.Statements.Sequence> aktivity a jsou korelována jako součást vzoru výměny zpráv žádost odpověď na serveru.

## <a name="the-receiveandsendreply-template"></a>Šablony ReceiveAndSendReply

Přidání **ReceiveAndSendReply** šablona dělá tři věci kromě vytvoření <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity s <xref:System.Activities.Statements.Sequence> aktivity:

- Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A> a <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> vlastnosti <xref:System.ServiceModel.Activities.Receive> aktivity.

- Vytvoří vazbu <xref:System.ServiceModel.Activities.SendReply.Request%2A> vlastnost <xref:System.ServiceModel.Activities.Receive> aktivitu <xref:System.ServiceModel.Activities.Send> aktivity.

- Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnná v Nadřazená aktivita.

### <a name="use-the-receiveandsendreply-template-designer"></a>Použijte návrhář šablony ReceiveAndSendReply

Přístup **ReceiveAndSendReply** návrháře aktivit v **zasílání zpráv** kategorii **nástrojů**. **ReceiveAndSendReply** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění bez ohledu na to aktivity jsou obvykle umístěny. Vyřazení Návrhář aktivity vytvoří <xref:System.ServiceModel.Activities.Receive> aktivitu, která se dá nakonfigurovat s **odeslat** návrháře aktivit a korelační <xref:System.ServiceModel.Activities.SendReply> , který se dá nakonfigurovat s SendReplyToReceive návrháře.

Další informace o používání **Receive** návrháře konfigurace <xref:System.ServiceModel.Activities.Receive> aktivity, naleznete v tématu [přijímat Návrhář aktivity](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Vlastnosti odeslání odpovědi SendReply

Následující tabulka ukazuje <xref:System.ServiceModel.Activities.SendReply> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností a můžete upravit některé na povrchu návrháře postupu provádění.


| Název vlastnosti | Požadováno | Použití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Volitelné jméno <xref:System.ServiceModel.Activities.SendReply> aktivity. Výchozí hodnota je SendReplyToReceive.<br /><br /> Ačkoli použití jinou než výchozí hodnotu pro popisný <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je vhodné použít taková hodnota. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | Hodnota TRUE | Odkaz <xref:System.ServiceModel.Activities.Receive> aktivity spárovat s tímto <xref:System.ServiceModel.Activities.SendReply> aktivity. Tato vlastnost nesmí být **null**. <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity se používají společně na serveru pro model vzorcem zasílání zpráv žádost odpověď. Tato vlastnost určuje, které <xref:System.ServiceModel.Activities.Send> spárované aktivity. V návrháři, nelze upravit tuto vlastnost, protože je automaticky vázán na <xref:System.ServiceModel.Activities.Send> aktivity, ze kterého jste vytvořili <xref:System.ServiceModel.Activities.SendReply> aktivity. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Určuje zprávu nebo parametr obsah, který se zobrazí. Může se jednat buď <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivity nebo <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivity. Tato vlastnost upravit kliknutím tlačítko se třemi tečkami vedle možnosti **obsahu** pole v mřížce vlastností nebo kliknutím **definovat** vedle **obsahu** popisek  **Přijímat** povrch návrháře aktivit. Obě zobrazení **definici obsahu** dialogového okna. Další informace o tom, jak pomocí tohoto políčka, najdete v článku [obsahu dialogové okno Definice](../workflow-designer/content-definition-dialog-box.md) tématu. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objekty, které inicializovat více <xref:System.ServiceModel.Activities.CorrelationHandle> objekty, které to nakonfigurovat <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu. Klikněte na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> vlastnost v mřížce vlastnosti otevřít **přidat inicializátory korelace** dialogové okno. Další informace o použití tohoto pole, najdete v článku [dialogové okno Přidat inicializátory korelace](../workflow-designer/add-correlationinitializers-dialog-box.md) tématu. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Určuje akci záhlaví zprávy. Pokud to není explicitně nastavena, její výchozí hodnotu:<br /><br /> <strong>https://tempuri.org/{service obor názvů kontraktu} / {název kontraktu služby} / {název operace}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Určuje, zda instance pracovního postupu by měl nastavit jako trvalý, před odesláním zprávy s odpovědí. Výchozí hodnota je **false**. |

## <a name="see-also"></a>Viz také:

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)