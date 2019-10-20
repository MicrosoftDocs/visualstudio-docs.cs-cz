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
ms.openlocfilehash: 4ecb0e201c4351a8a117d1e35aca97866b2beb89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663273"
---
# <a name="sendandreceivereply-template-designer"></a>Návrhář šablony SendAndReceiveReply
Šablona **SendAndReceiveReply** se používá k vytvoření páru předem konfigurovaných aktivit <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> v rámci <xref:System.Activities.Statements.Sequence> aktivity, které se korelují jako součást vzoru výměny zprávy žádosti nebo odpovědi na klientovi.

## <a name="the-sendandreceivereply-template"></a>Šablona SendAndReceiveReply
 Přidání šablony **SendAndReceiveReply** zahrnuje tři věci kromě vytváření <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivit v rámci <xref:System.Activities.Statements.Sequence> aktivity:

1. Nakonfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> vlastnosti aktivity <xref:System.ServiceModel.Activities.Send>.

2. Váže vlastnost <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> aktivity <xref:System.ServiceModel.Activities.ReceiveReply> na aktivitu <xref:System.ServiceModel.Activities.Send>.

3. Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnnou v nadřazené aktivitě.

### <a name="using-the-sendandreceivereply-template-designer"></a>Použití návrháře šablon SendAndReceiveReply
 Návrhář aktivity **SendAndReceiveReply** se dá najít v kategorii **zasílání zpráv** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** ze **zobrazení).** nebo CTRL + ALT + X.)

 Návrhář aktivity **SendAndReceiveReply** lze přetáhnout ze **sady nástrojů** a přetáhnout na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity. Tím se vytvoří <xref:System.ServiceModel.Activities.Send> aktivita, která se dá nakonfigurovat pomocí návrháře aktivity **odeslání** a korelační <xref:System.ServiceModel.Activities.ReceiveReply>, která se dá nakonfigurovat pomocí návrháře **ReceiveReplyForSend** .

 [!INCLUDE[crabout](../includes/crabout-md.md)] použití možnosti **Odeslat** návrháře ke konfiguraci aktivity <xref:System.ServiceModel.Activities.Send>, přečtěte si téma [odeslání](../workflow-designer/send-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] použití návrháře **ReceiveReplyForSend** ke konfiguraci aktivity <xref:System.ServiceModel.Activities.ReceiveReply>, přečtěte si následující část.

### <a name="properties-of-receivereply"></a>Vlastnosti ReceiveReply
 V následující tabulce jsou uvedeny vlastnosti <xref:System.ServiceModel.Activities.ReceiveReply> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé lze upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer ploše.

|                                 Název vlastnosti                                 | Požadováno |                                                                                                                                                                                                                                                                                                                                                        Použití                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Volitelný popisný název aktivity <xref:System.ServiceModel.Activities.ReceiveReply>. Výchozí hodnota je ReceiveReplyForSend.<br /><br /> I když použití jiné než výchozí hodnoty pro popisný <xref:System.Activities.Activity.DisplayName%2A> není naprosto povinné, je vhodné použít takovou hodnotu.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   Podmínka   | Odkaz na aktivitu <xref:System.ServiceModel.Activities.Send> spárované s touto aktivitou <xref:System.ServiceModel.Activities.ReceiveReply>. Tato vlastnost nesmí mít **hodnotu null**. Aktivity <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> se společně na klientovi používají k modelování vzoru zasílání zpráv požadavku a odpovědí. Tato vlastnost určuje, která aktivita <xref:System.ServiceModel.Activities.Send> se spáruje. V Návrháři tuto vlastnost nelze upravit, protože je automaticky svázána s aktivitou <xref:System.ServiceModel.Activities.Send>, ze které jste vytvořili aktivitu <xref:System.ServiceModel.Activities.ReceiveReply>. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Určuje zprávu nebo parametr obsahu, který se má přijmout. Může to být buď aktivita <xref:System.ServiceModel.Activities.ReceiveMessageContent>, nebo aktivita <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Tuto vlastnost upravíte kliknutím na tlačítko se třemi tečkami vedle pole **obsah** v mřížce vlastností nebo kliknutím na **definovat...** tlačítko vedle popisku **obsahu** na ploše návrháře aktivity **Receive** . V obou zobrazeních se zobrazí dialogové okno **definice obsahu** . [!INCLUDE[crabout](../includes/crabout-md.md)], jak používat toto pole, najdete v tématu věnovaném [definici obsahu v dialogovém okně](../workflow-designer/content-definition-dialog-box.md) .                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují více objektů <xref:System.ServiceModel.Activities.CorrelationHandle>, které konfigurují tuto <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle vlastnosti <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> v mřížce vlastnosti otevřete dialogové okno **Přidat Inicializátory korelace** . [!INCLUDE[crabout](../includes/crabout-md.md)] v tomto poli najdete v tématu věnovaném [dialogovému oknu Přidat inicializátoři CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Určuje hlavičku akce zprávy. Pokud není nastavena explicitně, jeho hodnota se nastaví jako výchozí:<br /><br /> <strong>https://tempuri.org/{service obor názvů kontraktu}/{Service název kontraktu}/{Operation název}.</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>Viz také
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)