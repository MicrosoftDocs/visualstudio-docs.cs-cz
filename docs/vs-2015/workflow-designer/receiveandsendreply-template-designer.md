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
ms.openlocfilehash: e853967f73c99aa52958754e9f59f644c2f9497b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672545"
---
# <a name="receiveandsendreply-template-designer"></a>Návrhář šablony ReceiveAndSendReply
Šablona **ReceiveAndSendReply** se používá k vytvoření páru předem konfigurovaných aktivit <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> v rámci <xref:System.Activities.Statements.Sequence> aktivity, které se korelují jako součást vzoru výměny zprávy žádosti nebo odpovědi na serveru.

## <a name="the-receiveandsendreply-template"></a>Šablona ReceiveAndSendReply
 Přidání šablony **ReceiveAndSendReply** zahrnuje tři věci kromě vytvoření <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity s <xref:System.Activities.Statements.Sequence> aktivitou:

1. Nakonfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> vlastnosti aktivity <xref:System.ServiceModel.Activities.Receive>.

2. Váže vlastnost <xref:System.ServiceModel.Activities.SendReply.Request%2A> aktivity <xref:System.ServiceModel.Activities.Receive> na aktivitu <xref:System.ServiceModel.Activities.Send>.

3. Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnnou v nadřazené aktivitě.

### <a name="using-the-receiveandsendreply-template-designer"></a>Použití návrháře šablon ReceiveAndSendReply
 Návrhář aktivity **ReceiveAndSendReply** se dá najít v kategorii **zasílání zpráv** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** v [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** ze **zobrazení).** nebo CTRL + ALT + X.)

 Návrhář aktivity **ReceiveAndSendReply** lze přetáhnout ze **sady nástrojů** a přetáhnout na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity. Tím se vytvoří <xref:System.ServiceModel.Activities.Receive> aktivita, která se dá nakonfigurovat pomocí návrháře aktivity **odeslání** a korelační <xref:System.ServiceModel.Activities.SendReply>, která se dá nakonfigurovat pomocí návrháře SendReplyToReceive.

 [!INCLUDE[crabout](../includes/crabout-md.md)] použití návrháře **Receive** ke konfiguraci aktivity <xref:System.ServiceModel.Activities.Receive>, přečtěte si téma [Receive](../workflow-designer/receive-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] použití návrháře **SendReplyToReceive** ke konfiguraci aktivity <xref:System.ServiceModel.Activities.SendReply>, přečtěte si následující část.

### <a name="properties-of-sendreply"></a>Vlastnosti pro aktivitu SendReply
 V následující tabulce jsou uvedeny vlastnosti <xref:System.ServiceModel.Activities.SendReply> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé lze upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] návrhové ploše.

|                               Název vlastnosti                                | Požadováno |                                                                                                                                                                                                                                                                                                                                                      Použití                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            Volitelný popisný název aktivity <xref:System.ServiceModel.Activities.SendReply>. Výchozí hodnota je SendReplyToReceive.<br /><br /> I když použití jiné než výchozí hodnoty pro popisný <xref:System.Activities.Activity.DisplayName%2A> není naprosto povinné, je vhodné použít takovou hodnotu.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   Podmínka   | Odkaz na aktivitu <xref:System.ServiceModel.Activities.Receive> spárované s touto aktivitou <xref:System.ServiceModel.Activities.SendReply>. Tato vlastnost nesmí mít **hodnotu null**. Aktivity <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> se na serveru používají k modelování vzoru zasílání zpráv požadavek/odpověď. Tato vlastnost určuje, která aktivita <xref:System.ServiceModel.Activities.Send> se spáruje. V Návrháři tuto vlastnost nelze upravit, protože je automaticky svázána s aktivitou <xref:System.ServiceModel.Activities.Send>, ze které jste vytvořili aktivitu <xref:System.ServiceModel.Activities.SendReply>. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Určuje zprávu nebo parametr obsahu, který se má přijmout. Může to být buď aktivita <xref:System.ServiceModel.Activities.ReceiveMessageContent>, nebo aktivita <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Tuto vlastnost upravíte kliknutím na tlačítko se třemi tečkami vedle pole **obsah** v mřížce vlastností nebo kliknutím na **definovat...** tlačítko vedle popisku **obsahu** na ploše návrháře aktivity **Receive** . V obou zobrazeních se zobrazí dialogové okno **definice obsahu** . [!INCLUDE[crabout](../includes/crabout-md.md)], jak používat toto pole, najdete v tématu věnovaném [definici obsahu v dialogovém okně](../workflow-designer/content-definition-dialog-box.md) .                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují více objektů <xref:System.ServiceModel.Activities.CorrelationHandle>, které konfigurují tuto <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle vlastnosti <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> v mřížce vlastnosti otevřete dialogové okno **Přidat Inicializátory korelace** . [!INCLUDE[crabout](../includes/crabout-md.md)] v tomto poli najdete v tématu věnovaném [dialogovému oknu Přidat inicializátoři CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Určuje hlavičku akce zprávy. Pokud není nastavena explicitně, jeho hodnota se nastaví jako výchozí:<br /><br /> <strong>https://tempuri.org/{service obor názvů kontraktu}/{Service název kontraktu}/{Operation}</strong>                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Určuje, zda má být instance pracovního postupu trvalá před odesláním zprávy s odpovědí. Výchozí hodnota je **false (NEPRAVDA**).                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Viz také
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)