---
title: Návrhář šablony ReceiveAndSendReply | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 52d52d95ea6efe66e4888bdb81a9ce86633e8c11
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935364"
---
# <a name="receiveandsendreply-template-designer"></a>Návrhář šablony ReceiveAndSendReply
**ReceiveAndSendReply** šablona se používá k vytvoření páru předem nakonfigurované <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity v rámci <xref:System.Activities.Statements.Sequence> aktivitu, která se korelují jako součást výměně zpráv žádost odpověď vzor na serveru.  

## <a name="the-receiveandsendreply-template"></a>Šablony ReceiveAndSendReply  
 Přidání **ReceiveAndSendReply** šablona dělá tři věci kromě vytvoření <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity se <xref:System.Activities.Statements.Sequence> aktivity:  

1.  Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> vlastnosti <xref:System.ServiceModel.Activities.Receive> aktivity.  

2.  Vytvoří vazbu <xref:System.ServiceModel.Activities.SendReply.Request%2A> vlastnost <xref:System.ServiceModel.Activities.Receive> aktivitu <xref:System.ServiceModel.Activities.Send> aktivity.  

3.  Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnná v Nadřazená aktivita.  

### <a name="using-the-receiveandsendreply-template-designer"></a>Pomocí návrháře šablony ReceiveAndSendReply  
 **ReceiveAndSendReply** návrháře aktivit najdete v **zasílání zpráv** kategorii **nástrojů**, který přistupuje po kliknutí **sady nástrojů**  kartu [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte možnost **nástrojů** z **zobrazení** nabídky nebo CTRL + ALT + X.)  

 **ReceiveAndSendReply** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřazené k [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface všude, kde aktivity jsou obvykle umístěny. Tím se vytvoří <xref:System.ServiceModel.Activities.Receive> aktivitu, která se dá nakonfigurovat s **odeslat** návrháře aktivit a korelační <xref:System.ServiceModel.Activities.SendReply> , který se dá nakonfigurovat s SendReplyToReceive návrháře.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] pomocí **Receive** návrháře konfigurace <xref:System.ServiceModel.Activities.Receive> aktivity, najdete v článku [Receive](../workflow-designer/receive-activity-designer.md) tématu.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] použití **SendReplyToReceive** návrháře konfigurace <xref:System.ServiceModel.Activities.SendReply> aktivity, naleznete v následující části.  

### <a name="properties-of-sendreply"></a>Vlastnosti odeslání odpovědi SendReply  
 Následující tabulka ukazuje <xref:System.ServiceModel.Activities.SendReply> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností a některé možné upravovat ve [!INCLUDE[wfd2](../includes/wfd2-md.md)] návrhové ploše.  


|                               Název vlastnosti                                | Požadováno |                                                                                                                                                                                                                                                                                                                                                      Použití                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            Volitelné jméno <xref:System.ServiceModel.Activities.SendReply> aktivity. Výchozí hodnota je SendReplyToReceive.<br /><br /> Ačkoli použití jinou než výchozí hodnotu pro popisný <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je vhodné použít taková hodnota.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   Hodnota TRUE   | Odkaz <xref:System.ServiceModel.Activities.Receive> aktivity spárovat s tímto <xref:System.ServiceModel.Activities.SendReply> aktivity. Tato vlastnost nesmí být **null**. <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity se používají společně na serveru pro model vzorcem zasílání zpráv žádost odpověď. Tato vlastnost určuje, které <xref:System.ServiceModel.Activities.Send> spárované aktivity. V návrháři, nelze upravit tuto vlastnost, protože je automaticky vázán na <xref:System.ServiceModel.Activities.Send> aktivity, ze kterého jste vytvořili <xref:System.ServiceModel.Activities.SendReply> aktivity. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Určuje zprávu nebo parametr obsah, který se zobrazí. Může se jednat buď <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivity nebo <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivity. Tato vlastnost upravit kliknutím na tlačítko se třemi tečkami vedle **obsahu** v mřížce vlastností nebo kliknutím **definovat...** tlačítko vedle **obsahu** popisek **Receive** povrch návrháře aktivit. Obě zobrazení **definici obsahu** dialogového okna. [!INCLUDE[crabout](../includes/crabout-md.md)] jak použít toto políčko, najdete v článku [obsahu dialogové okno Definice](../workflow-designer/content-definition-dialog-box.md) tématu.                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objekty, které inicializovat více <xref:System.ServiceModel.Activities.CorrelationHandle> objekty, které to nakonfigurovat <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu. Klikněte na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> vlastnost v mřížce vlastnosti otevřít **přidat inicializátory korelace** dialogové okno. [!INCLUDE[crabout](../includes/crabout-md.md)] Pomocí tohoto políčka, najdete v článku [dialogové okno Přidat inicializátory korelace](../workflow-designer/add-correlationinitializers-dialog-box.md) tématu.            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Určuje akci záhlaví zprávy. Pokud není explicitně nastavena, její výchozí hodnotu:<br /><br /> <strong>https://tempuri.org/{service obor názvů kontraktu} / {název kontraktu služby} / {název operace}</strong>                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Určuje, zda instance pracovního postupu by měl nastavit jako trvalý, před odesláním zprávy s odpovědí. Výchozí hodnota je **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Viz také  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Zobrazit](../workflow-designer/receive-activity-designer.md)   
 [Odeslat](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)