---
title: Návrhář šablony SendAndReceiveReply | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395341"
---
# <a name="sendandreceivereply-template-designer"></a>Návrhář šablony SendAndReceiveReply
Šablona **SendAndReceiveReply** se používá k vytvoření <xref:System.ServiceModel.Activities.Send> dvojice <xref:System.ServiceModel.Activities.ReceiveReply> předem <xref:System.Activities.Statements.Sequence> nakonfigurovaných a aktivit v rámci aktivity, které jsou korelovány jako součást vzoru výměny zpráv požadavek/odpověď na straně klienta.

## <a name="the-sendandreceivereply-template"></a>Šablona SendAndReceiveReply
 Přidání **SendAndReceiveReply** šablony provádí tři <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> věci kromě <xref:System.Activities.Statements.Sequence> vytváření a aktivity v rámci aktivity:

1. Konfiguruje vlastnosti <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> , aktivity. <xref:System.ServiceModel.Activities.Send>

2. Sváže <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> vlastnost aktivity <xref:System.ServiceModel.Activities.ReceiveReply> s <xref:System.ServiceModel.Activities.Send> aktivitou.

3. Vytvoří <xref:System.ServiceModel.Activities.CorrelationHandle> jako proměnnou v nadřazené aktivitě.

### <a name="using-the-sendandreceivereply-template-designer"></a>Použití návrháře šablon SendAndReceiveReply
 Návrhář aktivit **SendAndReceiveReply** najdete v kategorii **Zasílání zpráv** v **panelu nástrojů**, ke které se přistupuje kliknutím na [!INCLUDE[wfd2](../includes/wfd2-md.md)] kartu Panel **nástrojů** (Případně vyberte **panel nástrojů** z nabídky **Zobrazení** nebo CTRL+ALT+X.)

 **SendAndReceiveReply** návrháře aktivit lze přetáhnout z **panelu** [!INCLUDE[wfd2](../includes/wfd2-md.md)] nástrojů a spadl na povrch všude tam, kde jsou obvykle umístěny aktivity. Tím se <xref:System.ServiceModel.Activities.Send> vytvoří aktivita, která může být nakonfigurována pomocí návrháře aktivit **odesílání** a korelační, <xref:System.ServiceModel.Activities.ReceiveReply> kterou lze nakonfigurovat s návrhářem **ReceiveReplyForSend.**

 [!INCLUDE[crabout](../includes/crabout-md.md)]pomocí návrháře **odeslat** ke konfiguraci aktivity, <xref:System.ServiceModel.Activities.Send> naleznete v tématu [Odeslat.](../workflow-designer/send-activity-designer.md)

 [!INCLUDE[crabout](../includes/crabout-md.md)]pomocí návrháře **ReceiveReplyForSend** <xref:System.ServiceModel.Activities.ReceiveReply> ke konfiguraci aktivity naleznete v následující části.

### <a name="properties-of-receivereply"></a>Vlastnosti receivereply
 V následující tabulce <xref:System.ServiceModel.Activities.ReceiveReply> jsou uvedeny vlastnosti a popisuje, jak jsou používány v návrháři. Tyto vlastnosti lze upravovat v mřížce [!INCLUDE[wfd2](../includes/wfd2-md.md)]vlastností a některé lze upravovat na povrchu návrháře.

|                                 Název vlastnosti                                 | Požaduje se |                                                                                                                                                                                                                                                                                                                                                        Využití                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Volitelný popisný název <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. Výchozí hodnota je ReceiveReplyForSend.<br /><br /> Přestože použití hodnoty, která není <xref:System.Activities.Activity.DisplayName%2A> výchozí pro přívětivé, není nezbytně nutné, je osvědčeným postupem použít takovou hodnotu.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Odkaz na <xref:System.ServiceModel.Activities.Send> aktivitu <xref:System.ServiceModel.Activities.ReceiveReply> spárovanou s touto aktivitou. Tato vlastnost nesmí mít **hodnotu null**. <xref:System.ServiceModel.Activities.Send>a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity se používají společně na straně klienta k modelování vzoru zasílání zpráv požadavku a odpovědi. Tato vlastnost určuje, která <xref:System.ServiceModel.Activities.Send> aktivita je spárována. V návrháři nelze upravit tuto vlastnost, protože <xref:System.ServiceModel.Activities.Send> je automaticky vázána <xref:System.ServiceModel.Activities.ReceiveReply> na aktivitu, ze které jste aktivitu vytvořili. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Určuje zprávu nebo obsah parametrů, který má být přijímán. Může to být <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivita <xref:System.ServiceModel.Activities.ReceiveParametersContent> nebo aktivita. Upravte tuto vlastnost kliknutím na tlačítko elipsy vedle pole **Obsah** v mřížce vlastností nebo kliknutím na **definovat...** vedle popisku **Obsah** na povrchu návrháře **aktivit příjmu.** Obě zobrazí dialogové **okno Definice obsahu.** [!INCLUDE[crabout](../includes/crabout-md.md)]jak toto pole používat, přečtěte si téma [dialogového okna Definice obsahu.](../workflow-designer/content-definition-dialog-box.md)                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Receive> více objektů, které konfigurují tuto aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnosti v mřížce vlastností otevřete dialogové okno Přidat **intezivace korelace.** [!INCLUDE[crabout](../includes/crabout-md.md)]pomocí tohoto pole, viz [přidat korelaceInitializers dialogovéokno](../workflow-designer/add-correlationinitializers-dialog-box.md) téma.               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Určuje záhlaví akce zprávy. Pokud není explicitně nastavena, jeho hodnota je výchozí:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Viz také
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [initializecorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [receive](../workflow-designer/receive-activity-designer.md) [receiveandSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)