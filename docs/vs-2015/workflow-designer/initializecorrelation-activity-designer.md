---
title: Návrhář aktivity InitializeCorrelation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 145b67574169696771f4102b29e9dc8f6a9d1575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659025"
---
# <a name="initializecorrelation-activity-designer"></a>Návrhář aktivity InitializeCorrelation
Návrhář aktivity **InitializeCorrelation** slouží k vytvoření a konfiguraci aktivity <xref:System.ServiceModel.Activities.InitializeCorrelation>, která se používá k navázání korelace mezi zprávami před jejich odesláním nebo přijetím.

## <a name="the-initializecorrelation-activity"></a>Aktivita InitializeCorrelation
 @No__t_0 aktivita se používá k inicializaci korelací bez odeslání nebo přijetí zprávy. Při odesílání nebo přijímání zprávy se obvykle inicializuje korelace. Pokud musí být korelační zpráva navázána před odesláním nebo přijetím zprávy, použijte k inicializaci korelace <xref:System.ServiceModel.Activities.InitializeCorrelation>.

### <a name="using-the-initializecorrelation-activity-designer"></a>Pomocí návrháře aktivity InitializeCorrelation
 Návrhář aktivity **InitializeCorrelation** se dá najít v kategorii **zasílání zpráv** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v **zobrazení).** v nabídce nebo CTRL + ALT + X.)

 Návrhář aktivity **InitializeCorrelation** lze přetáhnout ze **sady nástrojů** a přetáhnout na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu. Tím se vytvoří aktivita <xref:System.ServiceModel.Activities.InitializeCorrelation> s výchozím <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation. <xref:System.Activities.Activity.DisplayName%2A> se dá upravit v hlavičce návrháře aktivity **InitializeCorrelation** nebo v poli **DisplayName** v okně **vlastnosti** .

 @No__t_0 může být určeno v poli **korelace** v okně **vlastnosti** na ploše návrháře aktivity **InitializeCorrelation** .

 Kliknutí na tlačítko se třemi tečkami vedle pole **CorrelationData** v okně **vlastnosti** nebo zobrazení... text nápovědy na ploše návrháře aktivit **InitializeCorrelation** zobrazuje dialogové okno **inicializovat korelaci** , ve kterém můžete zadat popisovač korelace a páry klíč-hodnota používané k jeho inicializaci. [!INCLUDE[crabout](../includes/crabout-md.md)] pomocí tohoto dialogového okna se přečtěte v tématu [dialogové okno Editor kolekcí typů](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Vlastnosti InitializeCorrelation
 V následující tabulce jsou uvedeny vlastnosti <xref:System.ServiceModel.Activities.InitializeCorrelation> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v okně **vlastnosti** nebo na [!INCLUDE[wfd2](../includes/wfd2-md.md)] ploše.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.ServiceModel.Activities.InitializeCorrelation>. Výchozí hodnota je InitializeCorrelation.<br /><br /> I když použití jiné než výchozí hodnoty pro popisný <xref:System.Activities.Activity.DisplayName%2A> není naprosto povinné, je vhodné použít takovou hodnotu.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|@No__t_0 slouží k přidružení aktivit pracovního postupu v korelaci.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Slovník dat korelace, který se týká zpráv instance pracovního postupu.<br /><br /> K nakonfigurování <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> použijte dialogové okno **inicializovat korelaci** . [!INCLUDE[crabout](../includes/crabout-md.md)] dialogovém okně použít tento dialog naleznete v tématu [dialogové okno Editor kolekcí typů](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Viz také
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)