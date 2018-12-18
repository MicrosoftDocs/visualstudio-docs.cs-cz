---
title: Návrhář aktivity Correlationscope | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 4a46c50a888808932d071622d83b871761977259
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173196"
---
# <a name="correlationscope-activity-designer"></a>Návrhář aktivity CorrelationScope
**CorrelationScope** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.ServiceModel.Activities.CorrelationScope> aktivitu, která poskytuje implicitní správu podřízených aktivit zasílání zpráv pomocí <xref:System.ServiceModel.Activities.CorrelationHandle> objektu.  
  
## <a name="the-correlationscope-activity"></a>Aktivity CorrelationScope  
 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> Určuje vlastnost <xref:System.ServiceModel.Activities.CorrelationHandle> používá ke správě podřízených aktivit zasílání zpráv. <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> aktivity obsažené v <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> jsou nakonfigurovány pro použití <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> vlastnosti nadřazeného <xref:System.ServiceModel.Activities.CorrelationScope> aktivita k provedení korelace.  
  
### <a name="using-the-correlationscope-activity-designer"></a>Pomocí aktivity Correlationscope  
 **CorrelationScope** návrháře aktivit najdete v **zasílání zpráv** kategorii **nástrojů**, který přistupuje po kliknutí **nástrojů** karty na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte možnost **nástrojů** z **zobrazení** nabídky nebo CTRL + ALT + X.)  
  
 **CorrelationScope** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřazené k [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu. Tím se vytvoří <xref:System.ServiceModel.Activities.CorrelationScope> aktivity s výchozím **DisplayName** z CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A> Můžete upravovat v záhlaví **CorrelationScope** Návrhář aktivity nebo **DisplayName** pomocí boxingu **vlastnosti** okno.  
  
 Chcete-li určit <xref:System.ServiceModel.Activities.CorrelationHandle> používají podřízené aktivity zasílání zpráv, klikněte na tlačítko se třemi tečkami vedle **CorrelatesWith** pole v **vlastnosti** okno k zobrazení **Editor výrazů**  dialogové okno. Tuto vlastnost můžete také nastavit na plochu návrháře aktivit.  
  
 Aktivity s rozsahem v rámci korelace jsou určeny umístěním jejich návrháře v rámci **tělo** pole v rámci **CorrelationScope** návrháře.  
  
### <a name="the-correlationscope-properties"></a>Vlastnosti CorrelationScope  
 Následující tabulka ukazuje <xref:System.ServiceModel.Activities.CorrelationScope> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v **vlastnosti** okno nebo na [!INCLUDE[wfd2](../includes/wfd2-md.md)] návrháře surface a často v obou.  
  
|Název vlastnosti|Požadováno|Použití|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Volitelné jméno <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Určuje, <xref:System.ServiceModel.Activities.CorrelationHandle> používá ke správě podřízených aktivit zasílání zpráv. Pokud tuto vlastnost nenastavíte <xref:System.ServiceModel.Activities.CorrelationScope> vytvoří implicitní <xref:System.ServiceModel.Activities.CorrelationHandle> automaticky.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Určuje aktivity v rámci rozsahu korelace.|  
  
## <a name="see-also"></a>Viz také  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Zobrazit](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Odeslat](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)