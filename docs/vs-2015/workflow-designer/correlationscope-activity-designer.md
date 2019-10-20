---
title: Návrhář aktivity CorrelationScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6ffcfd63d60ab6f085b5cb2a793e8bf17a50d8e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656916"
---
# <a name="correlationscope-activity-designer"></a>Návrhář aktivity CorrelationScope
Návrhář aktivity **CorrelationScope** slouží k vytvoření a konfiguraci aktivity <xref:System.ServiceModel.Activities.CorrelationScope>, která poskytuje implicitní správu aktivit podřízeného zasílání zpráv pomocí objektu <xref:System.ServiceModel.Activities.CorrelationHandle>.

## <a name="the-correlationscope-activity"></a>Aktivita CorrelationScope
 Vlastnost <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> určuje <xref:System.ServiceModel.Activities.CorrelationHandle>, která se používá ke správě podřízených aktivit zasílání zpráv. Aktivity <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> obsažené v <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> jsou nakonfigurovány tak, aby pro provádění korelace používaly vlastnost <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> aktivity obsahující <xref:System.ServiceModel.Activities.CorrelationScope>.

### <a name="using-the-correlationscope-activity-designer"></a>Pomocí návrháře aktivity CorrelationScope
 Návrhář aktivity **CorrelationScope** se dá najít v kategorii **zasílání zpráv** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte **panel nástrojů** z V nabídce **Zobrazit** nebo CTRL + ALT + X.)

 Návrhář aktivity **CorrelationScope** lze přetáhnout ze **sady nástrojů** a přetáhnout na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu. Tím se vytvoří aktivita <xref:System.ServiceModel.Activities.CorrelationScope> s výchozím **názvem DisplayName** CorrelationScope. @No__t_0 lze upravit v hlavičce návrháře aktivity **CorrelationScope** nebo v poli **DisplayName** v okně **vlastnosti** .

 Chcete-li určit <xref:System.ServiceModel.Activities.CorrelationHandle> používané aktivitami podřízeného zasílání zpráv, klikněte na tlačítko se třemi tečkami vedle pole **popisovač CorrelatesWith** v okně **vlastnosti** . zobrazí se dialogové okno **Editor výrazů** . Tuto vlastnost lze také nastavit na ploše návrháře aktivit.

 Aktivity v oboru v rámci korelace jsou určeny tak, že se jejich návrháři vyřadí do pole **text** v rámci **CorrelationScope** designeru.

### <a name="the-correlationscope-properties"></a>Vlastnosti CorrelationScope
 V následující tabulce jsou uvedeny vlastnosti <xref:System.ServiceModel.Activities.CorrelationScope> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit buď v okně **vlastnosti** , nebo na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu návrháře a často v obou.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Volitelný popisný název aktivity <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Určuje <xref:System.ServiceModel.Activities.CorrelationHandle> pro správu aktivit podřízeného zasílání zpráv. Pokud tuto vlastnost nenastavíte, <xref:System.ServiceModel.Activities.CorrelationScope> automaticky vytvoří implicitní <xref:System.ServiceModel.Activities.CorrelationHandle>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Určuje aktivity v oboru korelace.|

## <a name="see-also"></a>Viz také
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)