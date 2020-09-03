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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658935"
---
# <a name="messaging-activity-designers"></a>Návrháři aktivit zasílání zpráv
Návrháři aktivity zasílání zpráv slouží k vytváření a konfiguraci aktivit zasílání zpráv, které odesílají a přijímají [!INCLUDE[indigo1](../includes/indigo1-md.md)] zprávy v rámci [!INCLUDE[wf](../includes/wf-md.md)] aplikace. [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)]Představuje pět aktivit zasílání zpráv a [!INCLUDE[wfd1](../includes/wfd1-md.md)] nabízí dva nové návrháře šablon, které vám umožní spravovat zprávy v rámci pracovního postupu. Témata obsažená v této části a uvedená v následující tabulce obsahují pokyny k používání [!INCLUDE[wfd2](../includes/wfd2-md.md)] návrháře aktivit a šablon.

## <a name="in-this-section"></a>V tomto oddílu

|Aktivita zprávy|Popis|
|----------------------|-----------------|
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Vytvoří a nakonfiguruje <xref:System.ServiceModel.Activities.CorrelationScope> aktivitu, která poskytuje implicitní správu podřízených aktivit zasílání zpráv s <xref:System.ServiceModel.Activities.CorrelationHandle> objektem.|
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Vytvoří a nakonfiguruje <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivitu, která se používá k inicializaci korelace bez odeslání nebo přijetí zprávy.|
|[Přijmout](../workflow-designer/receive-activity-designer.md)|Vytvoří a nakonfiguruje <xref:System.ServiceModel.Activities.Receive> aktivitu, která přijímá zprávu od služby.|
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Vytvoří předem nakonfigurovanou dvojici <xref:System.ServiceModel.Activities.Send> aktivit a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity v rámci <xref:System.Activities.Statements.Sequence> aktivity.|
|[Odeslat](../workflow-designer/send-activity-designer.md)|Vytvoří a nakonfiguruje <xref:System.ServiceModel.Activities.Send> aktivitu, která odešle zprávu službě.|
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Vytvoří předem nakonfigurovanou dvojici <xref:System.ServiceModel.Activities.Receive> aktivit a <xref:System.ServiceModel.Activities.SendReply> aktivity v rámci <xref:System.Activities.Statements.Sequence> aktivity.|
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Vytvoří a nakonfiguruje <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivitu, která umožňuje tok transakcí do pracovního postupu.|

## <a name="reference"></a>Referenční informace
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

 [Primitiva](../workflow-designer/primitives-activity-designers.md)

 [Transakce](../workflow-designer/transaction-activity-designers.md)

 [Kolekce](../workflow-designer/collection-activity-designers.md)

 [Zpracování chyb](../workflow-designer/error-handling-activity-designers.md)

## <a name="external-resources"></a>Externí zdroje
 [Používání návrhářů aktivit](../workflow-designer/using-the-activity-designers.md)