---
title: Návrháři aktivity zasílání zpráv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6fb06bea4cebf2558990d23f7ece5b4f8db5b95
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658935"
---
# <a name="messaging-activity-designers"></a>Návrháři aktivit zasílání zpráv
Návrháři aktivity zasílání zpráv slouží k vytváření a konfiguraci aktivit zasílání zpráv, které odesílají a získávají zprávy [!INCLUDE[indigo1](../includes/indigo1-md.md)] v rámci [!INCLUDE[wf](../includes/wf-md.md)] aplikace. @No__t_0 zavádí pět aktivit zasílání zpráv a [!INCLUDE[wfd1](../includes/wfd1-md.md)] poskytuje dva nové návrháře šablon, kteří vám umožní spravovat zprávy v rámci pracovního postupu. Témata obsažená v této části a uvedená v následující tabulce obsahují pokyny k použití [!INCLUDE[wfd2](../includes/wfd2-md.md)] a návrháře šablon.

## <a name="in-this-section"></a>V tomto oddílu

|Aktivita zprávy|Popis|
|----------------------|-----------------|
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Vytvoří a nakonfiguruje aktivitu <xref:System.ServiceModel.Activities.CorrelationScope>, která poskytuje implicitní správu podřízených aktivit zasílání zpráv s objektem <xref:System.ServiceModel.Activities.CorrelationHandle>.|
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Vytvoří a nakonfiguruje aktivitu <xref:System.ServiceModel.Activities.InitializeCorrelation>, která se používá k inicializaci korelace bez odeslání nebo přijetí zprávy.|
|[Receive](../workflow-designer/receive-activity-designer.md)|Vytvoří a nakonfiguruje aktivitu <xref:System.ServiceModel.Activities.Receive>, která přijímá zprávu od služby.|
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Vytvoří předem nakonfigurovanou dvojici aktivit <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> v rámci aktivity <xref:System.Activities.Statements.Sequence>.|
|[Send](../workflow-designer/send-activity-designer.md)|Vytvoří a nakonfiguruje aktivitu <xref:System.ServiceModel.Activities.Send>, která odešle zprávu službě.|
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Vytvoří předem nakonfigurovanou dvojici aktivit <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> v rámci aktivity <xref:System.Activities.Statements.Sequence>.|
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Vytvoří a nakonfiguruje aktivitu <xref:System.ServiceModel.Activities.TransactedReceiveScope>, která umožňuje tok transakcí do pracovního postupu.|

## <a name="reference"></a>Odkaz
 <xref:System.Activities.Activity>

 <xref:System.ServiceModel.Activities.CorrelationScope>

 <xref:System.ServiceModel.Activities.Receive>

 <xref:System.ServiceModel.Activities.Send>

 <xref:System.ServiceModel.Activities.ReceiveReply>

 <xref:System.ServiceModel.Activities.SendReply>

 <xref:System.ServiceModel.Activities.TransactedReceiveScope>

## <a name="related-sections"></a>Související oddíly
 Další typy návrháře aktivit najdete v následujících tématech.

 [Tok řízení](../workflow-designer/control-flow-activity-designers.md)

 [Používání návrhářů aktivit](../workflow-designer/using-the-activity-designers.md)

 [Vývojový diagram](../workflow-designer/flowchart-activity-designers.md)

 [Modul runtime](../workflow-designer/runtime-activity-designers.md)

 [Primitivní elementy](../workflow-designer/primitives-activity-designers.md)

 [Transakce](../workflow-designer/transaction-activity-designers.md)

 [Kolekce](../workflow-designer/collection-activity-designers.md)

 [Zpracování chyb](../workflow-designer/error-handling-activity-designers.md)

## <a name="external-resources"></a>Externí zdroje
 [Používání návrhářů aktivit](../workflow-designer/using-the-activity-designers.md)