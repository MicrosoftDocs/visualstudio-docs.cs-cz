---
title: Návrhář šablony ReceiveAndSendReply | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395394"
---
# <a name="receiveandsendreply-template-designer"></a>Návrhář šablony ReceiveAndSendReply
Šablona **ReceiveAndSendReply** se používá k vytvoření <xref:System.ServiceModel.Activities.Receive> dvojice <xref:System.ServiceModel.Activities.SendReply> předem <xref:System.Activities.Statements.Sequence> nakonfigurovaných a aktivit v rámci aktivity, které jsou korelovány jako součást vzoru výměny zpráv požadavku a odpovědi na serveru.

## <a name="the-receiveandsendreply-template"></a>Šablona ReceiveAndSendReply
 Přidání **ReceiveAndSendReply** šablony provádí tři <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> věci kromě <xref:System.Activities.Statements.Sequence> vytváření a aktivity s aktivitou:

1. Konfiguruje vlastnosti <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> , aktivity. <xref:System.ServiceModel.Activities.Receive>

2. Sváže <xref:System.ServiceModel.Activities.SendReply.Request%2A> vlastnost aktivity <xref:System.ServiceModel.Activities.Receive> s <xref:System.ServiceModel.Activities.Send> aktivitou.

3. Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnnou v nadřazené aktivitě.

### <a name="using-the-receiveandsendreply-template-designer"></a>Použití návrháře šablon ReceiveAndSendReply
 Návrhář aktivit **ReceiveAndSendReply** najdete v kategorii **Zasílání zpráv** v **panelu nástrojů**, ke které se přistupuje kliknutím na kartu Panel **nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Případně vyberte panel **nástrojů** z nabídky **Zobrazení** nebo CTRL+ALT+X.)

 **ReceiveAndSendReply** návrháře aktivit lze přetáhnout z **panelu** [!INCLUDE[wfd2](../includes/wfd2-md.md)] nástrojů a spadl na povrch všude tam, kde jsou obvykle umístěny aktivity. Tím se <xref:System.ServiceModel.Activities.Receive> vytvoří aktivita, která může být nakonfigurována s návrhářem **aktivity Odeslat** a korelační, <xref:System.ServiceModel.Activities.SendReply> kterou lze nakonfigurovat pomocí návrháře SendReplyToReceive.

 [!INCLUDE[crabout](../includes/crabout-md.md)]pomocí **Návrhář příjmu** ke <xref:System.ServiceModel.Activities.Receive> konfiguraci aktivity, naleznete v tématu [Příjem.](../workflow-designer/receive-activity-designer.md)

 [!INCLUDE[crabout](../includes/crabout-md.md)]pomocí návrháře **SendReplyToReceive** <xref:System.ServiceModel.Activities.SendReply> ke konfiguraci aktivity naleznete v následující části.

### <a name="properties-of-sendreply"></a>Vlastnosti SendReply
 V následující tabulce <xref:System.ServiceModel.Activities.SendReply> jsou uvedeny vlastnosti a popisuje, jak jsou používány v návrháři. Tyto vlastnosti lze upravovat v mřížce [!INCLUDE[wfd2](../includes/wfd2-md.md)] vlastností a některé lze upravovat na povrchu návrháře.

|                               Název vlastnosti                                | Požaduje se |                                                                                                                                                                                                                                                                                                                                                      Využití                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            Volitelný popisný název <xref:System.ServiceModel.Activities.SendReply> aktivity. Výchozí hodnota je SendReplyToReceive.<br /><br /> Přestože použití hodnoty, která není <xref:System.Activities.Activity.DisplayName%2A> výchozí pro přívětivé, není nezbytně nutné, je osvědčeným postupem použít takovou hodnotu.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | Odkaz na <xref:System.ServiceModel.Activities.Receive> aktivitu <xref:System.ServiceModel.Activities.SendReply> spárovanou s touto aktivitou. Tato vlastnost nesmí mít **hodnotu null**. <xref:System.ServiceModel.Activities.Receive>a <xref:System.ServiceModel.Activities.SendReply> aktivity se používají společně na serveru k modelování vzoru zasílání zpráv požadavku a odpovědi. Tato vlastnost určuje, která <xref:System.ServiceModel.Activities.Send> aktivita je spárována. V návrháři nelze upravit tuto vlastnost, protože <xref:System.ServiceModel.Activities.Send> je automaticky vázána <xref:System.ServiceModel.Activities.SendReply> na aktivitu, ze které jste aktivitu vytvořili. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Určuje zprávu nebo obsah parametrů, který má být přijímán. Může to být <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivita <xref:System.ServiceModel.Activities.ReceiveParametersContent> nebo aktivita. Upravte tuto vlastnost kliknutím na tlačítko elipsy vedle pole **Obsah** v mřížce vlastností nebo kliknutím na **definovat...** vedle popisku **Obsah** na povrchu návrháře **aktivit příjmu.** Obě zobrazí dialogové **okno Definice obsahu.** [!INCLUDE[crabout](../includes/crabout-md.md)]jak toto pole používat, přečtěte si téma [dialogového okna Definice obsahu.](../workflow-designer/content-definition-dialog-box.md)                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Receive> více objektů, které konfigurují tuto aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> vlastnosti v mřížce vlastností otevřete dialogové okno Přidat **intezivace korelace.** [!INCLUDE[crabout](../includes/crabout-md.md)]pomocí tohoto pole, viz [přidat korelaceInitializers dialogovéokno](../workflow-designer/add-correlationinitializers-dialog-box.md) téma.            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Určuje záhlaví akce zprávy. Pokud není explicitně nastavena, jeho hodnota je výchozí:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Určuje, zda má být instance pracovního postupu před odesláním zprávy s odpovědí zachována. Výchozí hodnota je **false** (nepravda).                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Viz také
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [SendSendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md)