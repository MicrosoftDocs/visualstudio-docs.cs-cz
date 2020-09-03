---
title: Návrhář šablon ReceiveAndSendReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c00eed244867cfd38b20f6a8f065fc6da006801
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395394"
---
# <a name="receiveandsendreply-template-designer"></a>Návrhář šablony ReceiveAndSendReply
Šablona **ReceiveAndSendReply** se používá k vytvoření dvojice předem nakonfigurovaných <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> aktivit a aktivit v rámci <xref:System.Activities.Statements.Sequence> aktivity, která se koreluje jako součást vzoru výměny zprávy žádosti nebo odpovědi na serveru.

## <a name="the-receiveandsendreply-template"></a>Šablona ReceiveAndSendReply
 Přidání šablony **ReceiveAndSendReply** provede tři věci Kromě vytváření <xref:System.ServiceModel.Activities.Receive> aktivit a <xref:System.ServiceModel.Activities.SendReply> aktivity s <xref:System.Activities.Statements.Sequence> aktivitou:

1. Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> vlastnosti <xref:System.ServiceModel.Activities.Receive> aktivity.

2. Váže <xref:System.ServiceModel.Activities.SendReply.Request%2A> vlastnost <xref:System.ServiceModel.Activities.Receive> aktivity na <xref:System.ServiceModel.Activities.Send> aktivitu.

3. Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnnou v nadřazené aktivitě.

### <a name="using-the-receiveandsendreply-template-designer"></a>Použití návrháře šablon ReceiveAndSendReply
 Návrhář aktivity **ReceiveAndSendReply** se dá najít v kategorii **zasílání zpráv** na **panelu nástrojů**, ke které se dostanete tak, že kliknete na kartu **panelu nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář aktivity **ReceiveAndSendReply** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity. Tím se vytvoří <xref:System.ServiceModel.Activities.Receive> aktivita, která se dá nakonfigurovat pomocí návrháře aktivity **odeslání** a korelace <xref:System.ServiceModel.Activities.SendReply> , která se dá nakonfigurovat pomocí návrháře SendReplyToReceive.

 [!INCLUDE[crabout](../includes/crabout-md.md)] použití nástroje **Receive** Designer ke konfiguraci <xref:System.ServiceModel.Activities.Receive> aktivity najdete v tématu věnovaném [příjmu](../workflow-designer/receive-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] Konfigurace aktivity pomocí návrháře **SendReplyToReceive** naleznete v <xref:System.ServiceModel.Activities.SendReply> následující části.

### <a name="properties-of-sendreply"></a>Vlastnosti pro aktivitu SendReply
 V následující tabulce jsou uvedeny <xref:System.ServiceModel.Activities.SendReply> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé lze upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] návrhové ploše.

|                               Název vlastnosti                                | Požaduje se |                                                                                                                                                                                                                                                                                                                                                      Využití                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  Ne   |                                                                                                                                                                                            Volitelný popisný název <xref:System.ServiceModel.Activities.SendReply> aktivity. Výchozí hodnota je SendReplyToReceive.<br /><br /> I když použití jiné než výchozí hodnoty pro popis není <xref:System.Activities.Activity.DisplayName%2A> bezpodmínečně nutné, jedná se o osvědčený postup pro použití takové hodnoty.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   Ano   | Odkaz na <xref:System.ServiceModel.Activities.Receive> aktivitu spárované s touto <xref:System.ServiceModel.Activities.SendReply> aktivitou Tato vlastnost nesmí mít **hodnotu null**. <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity se společně na serveru používají k modelování vzoru zasílání zpráv požadavku a odpovědí. Tato vlastnost určuje, která <xref:System.ServiceModel.Activities.Send> aktivita se spáruje. V Návrháři tuto vlastnost nelze upravit, protože je automaticky svázána s <xref:System.ServiceModel.Activities.Send> aktivitou, ze které jste <xref:System.ServiceModel.Activities.SendReply> aktivitu vytvořili. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  Ne   |                       Určuje zprávu nebo parametr obsahu, který se má přijmout. Může to být buď <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivita, nebo <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivita. Tuto vlastnost upravíte kliknutím na tlačítko se třemi tečkami vedle pole **obsah** v mřížce vlastností nebo kliknutím na **definovat...** tlačítko vedle popisku **obsahu** na ploše návrháře aktivity **Receive** . V obou zobrazeních se zobrazí dialogové okno **definice obsahu** . [!INCLUDE[crabout](../includes/crabout-md.md)] Jak používat toto pole, viz téma [definice obsahu](../workflow-designer/content-definition-dialog-box.md) v tématu.                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  Ne   |            Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují více <xref:System.ServiceModel.Activities.CorrelationHandle> objektů, které konfigurují tuto <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> vlastnosti v mřížce vlastnosti otevřete dialogové okno **Přidat Inicializátory korelace** . [!INCLUDE[crabout](../includes/crabout-md.md)] pomocí tohoto pole si přečtěte téma [Přidání dialogového okna inicializátoři CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  Ne   |                                                                                                                                                                                                                                              Určuje hlavičku akce zprávy. Pokud není nastavena explicitně, jeho hodnota se nastaví jako výchozí:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  Ne   |                                                                                                                                                                                                                                                                                          Určuje, zda má být instance pracovního postupu trvalá před odesláním zprávy s odpovědí. Výchozí hodnota je **false** (nepravda).                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Viz také
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)