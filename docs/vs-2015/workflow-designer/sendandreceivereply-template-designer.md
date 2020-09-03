---
title: Návrhář šablon SendAndReceiveReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395341"
---
# <a name="sendandreceivereply-template-designer"></a>Návrhář šablony SendAndReceiveReply
Šablona **SendAndReceiveReply** se používá k vytvoření dvojice předem nakonfigurovaných <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> aktivit a aktivit v rámci <xref:System.Activities.Statements.Sequence> aktivity, která se koreluje jako součást vzoru výměny zprávy žádosti nebo odpovědi na klientovi.

## <a name="the-sendandreceivereply-template"></a>Šablona SendAndReceiveReply
 Přidání šablony **SendAndReceiveReply** provede tři věci Kromě vytváření <xref:System.ServiceModel.Activities.Send> aktivit a <xref:System.ServiceModel.Activities.ReceiveReply> v rámci <xref:System.Activities.Statements.Sequence> aktivity:

1. Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> vlastnosti <xref:System.ServiceModel.Activities.Send> aktivity.

2. Váže <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> vlastnost <xref:System.ServiceModel.Activities.ReceiveReply> aktivity na <xref:System.ServiceModel.Activities.Send> aktivitu.

3. Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnnou v nadřazené aktivitě.

### <a name="using-the-sendandreceivereply-template-designer"></a>Použití návrháře šablon SendAndReceiveReply
 Návrhář aktivity **SendAndReceiveReply** se dá najít v kategorii **zasílání zpráv** na **panelu nástrojů**, ke které se dostanete tak, že kliknete na kartu **panel nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář aktivity **SendAndReceiveReply** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity. Tím se vytvoří <xref:System.ServiceModel.Activities.Send> aktivita, která se dá nakonfigurovat pomocí návrháře aktivity **odeslání** a korelace <xref:System.ServiceModel.Activities.ReceiveReply> , která se dá nakonfigurovat pomocí návrháře **ReceiveReplyForSend** .

 [!INCLUDE[crabout](../includes/crabout-md.md)]informace o **Send** konfiguraci aktivity pomocí návrháře odeslání <xref:System.ServiceModel.Activities.Send> najdete v tématu [odeslání](../workflow-designer/send-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] Konfigurace aktivity pomocí návrháře **ReceiveReplyForSend** naleznete v <xref:System.ServiceModel.Activities.ReceiveReply> následující části.

### <a name="properties-of-receivereply"></a>Vlastnosti ReceiveReply
 V následující tabulce jsou uvedeny <xref:System.ServiceModel.Activities.ReceiveReply> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé lze upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] návrhové ploše.

|                                 Název vlastnosti                                 | Požaduje se |                                                                                                                                                                                                                                                                                                                                                        Využití                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  Ne   |                                                                                                                                                                                            Volitelný popisný název <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. Výchozí hodnota je ReceiveReplyForSend.<br /><br /> I když použití jiné než výchozí hodnoty pro popis není <xref:System.Activities.Activity.DisplayName%2A> bezpodmínečně nutné, jedná se o osvědčený postup pro použití takové hodnoty.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   Ano   | Odkaz na <xref:System.ServiceModel.Activities.Send> aktivitu spárované s touto <xref:System.ServiceModel.Activities.ReceiveReply> aktivitou Tato vlastnost nesmí mít **hodnotu null**. <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity se v klientovi používají k modelování vzoru zasílání zpráv požadavek/odpověď. Tato vlastnost určuje, která <xref:System.ServiceModel.Activities.Send> aktivita se spáruje. V Návrháři tuto vlastnost nelze upravit, protože je automaticky svázána s <xref:System.ServiceModel.Activities.Send> aktivitou, ze které jste <xref:System.ServiceModel.Activities.ReceiveReply> aktivitu vytvořili. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  Ne   |                        Určuje zprávu nebo parametr obsahu, který se má přijmout. Může to být buď <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivita, nebo <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivita. Tuto vlastnost upravíte kliknutím na tlačítko se třemi tečkami vedle pole **obsah** v mřížce vlastností nebo kliknutím na **definovat...** tlačítko vedle popisku **obsahu** na ploše návrháře aktivity **Receive** . V obou zobrazeních se zobrazí dialogové okno **definice obsahu** . [!INCLUDE[crabout](../includes/crabout-md.md)] Jak používat toto pole, viz téma [definice obsahu](../workflow-designer/content-definition-dialog-box.md) v tématu.                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  Ne   |              Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují více <xref:System.ServiceModel.Activities.CorrelationHandle> objektů, které konfigurují tuto <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnosti v mřížce vlastnosti otevřete dialogové okno **Přidat Inicializátory korelace** . [!INCLUDE[crabout](../includes/crabout-md.md)] pomocí tohoto pole si přečtěte téma [Přidání dialogového okna inicializátoři CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  Ne   |                                                                                                                                                                                                                                               Určuje hlavičku akce zprávy. Pokud není nastavena explicitně, jeho hodnota se nastaví jako výchozí:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Viz také
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)