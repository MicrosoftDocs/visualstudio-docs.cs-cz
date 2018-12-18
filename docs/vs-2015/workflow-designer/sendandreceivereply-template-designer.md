---
title: Návrhář šablony SendAndReceiveReply | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: e2b7ffb52979c0899949806ae97b562f76b0b3c9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884950"
---
# <a name="sendandreceivereply-template-designer"></a>Návrhář šablony SendAndReceiveReply
**SendAndReceiveReply** šablona se používá k vytvoření páru předem nakonfigurované <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity v rámci <xref:System.Activities.Statements.Sequence> aktivitu, která se korelují jako součást výměně zpráv žádost odpověď vzor na straně klienta.  

## <a name="the-sendandreceivereply-template"></a>Šablony SendAndReceiveReply  
 Přidání **SendAndReceiveReply** šablona dělá tři věci kromě vytvoření <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity v rámci <xref:System.Activities.Statements.Sequence> aktivity:  

1.  Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> vlastnosti <xref:System.ServiceModel.Activities.Send> aktivity.  

2.  Vytvoří vazbu <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> vlastnost <xref:System.ServiceModel.Activities.ReceiveReply> aktivitu <xref:System.ServiceModel.Activities.Send> aktivity.  

3.  Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnná v Nadřazená aktivita.  

### <a name="using-the-sendandreceivereply-template-designer"></a>Pomocí návrháře šablony SendAndReceiveReply  
 **SendAndReceiveReply** návrháře aktivit najdete v **zasílání zpráv** kategorii **nástrojů**, který přistupuje po kliknutí **sady nástrojů**  kartě [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte možnost **nástrojů** z **zobrazení** nabídky nebo CTRL + ALT + X.)  

 **SendAndReceiveReply** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřazené k [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface všude, kde aktivity jsou obvykle umístěny. Tím se vytvoří <xref:System.ServiceModel.Activities.Send> aktivitu, která se dá nakonfigurovat s **odeslat** návrháře aktivit a korelační <xref:System.ServiceModel.Activities.ReceiveReply> , který se dá nakonfigurovat s **ReceiveReplyForSend** návrháře.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] pomocí **odeslat** návrháře konfigurace <xref:System.ServiceModel.Activities.Send> aktivity, najdete v článku [odeslat](../workflow-designer/send-activity-designer.md) tématu.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] použití **ReceiveReplyForSend** návrháře konfigurace <xref:System.ServiceModel.Activities.ReceiveReply> aktivity, naleznete v následující části.  

### <a name="properties-of-receivereply"></a>Vlastnosti ReceiveReply  
 Následující tabulka ukazuje <xref:System.ServiceModel.Activities.ReceiveReply> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností a některé možné upravovat ve [!INCLUDE[wfd2](../includes/wfd2-md.md)]návrhové ploše.  


|                                 Název vlastnosti                                 | Požadováno |                                                                                                                                                                                                                                                                                                                                                        Použití                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Volitelné jméno <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. Výchozí hodnota je ReceiveReplyForSend.<br /><br /> Ačkoli použití jinou než výchozí hodnotu pro popisný <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je vhodné použít taková hodnota.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   Hodnota TRUE   | Odkaz <xref:System.ServiceModel.Activities.Send> aktivity spárovat s tímto <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. Tato vlastnost nesmí být **null**. <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity se používají společně na straně klienta pro model vzorcem zasílání zpráv žádost odpověď. Tato vlastnost určuje, které <xref:System.ServiceModel.Activities.Send> spárované aktivity. V návrháři, nelze upravit tuto vlastnost, protože je automaticky vázán na <xref:System.ServiceModel.Activities.Send> aktivity, ze kterého jste vytvořili <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Určuje zprávu nebo parametr obsah, který se zobrazí. Může se jednat buď <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivity nebo <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivity. Tato vlastnost upravit kliknutím na tlačítko se třemi tečkami vedle **obsahu** v mřížce vlastností nebo kliknutím **definovat...** tlačítko vedle **obsahu** popisek **Receive** povrch návrháře aktivit. Obě zobrazení **definici obsahu** dialogového okna. [!INCLUDE[crabout](../includes/crabout-md.md)] jak použít toto políčko, najdete v článku [obsahu dialogové okno Definice](../workflow-designer/content-definition-dialog-box.md) tématu.                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objekty, které inicializovat více <xref:System.ServiceModel.Activities.CorrelationHandle> objekty, které to nakonfigurovat <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu. Klikněte na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnost v mřížce vlastnosti otevřít **přidat inicializátory korelace** dialogové okno. [!INCLUDE[crabout](../includes/crabout-md.md)] Pomocí tohoto políčka, najdete v článku [dialogové okno Přidat inicializátory korelace](../workflow-designer/add-correlationinitializers-dialog-box.md) tématu.               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Určuje akci záhlaví zprávy. Pokud není explicitně nastavena, její výchozí hodnotu:<br /><br /> <strong>https://tempuri.org/{service obor názvů kontraktu} / {název kontraktu služby} / {název operace}.</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>Viz také  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Zobrazit](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Odeslat](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)