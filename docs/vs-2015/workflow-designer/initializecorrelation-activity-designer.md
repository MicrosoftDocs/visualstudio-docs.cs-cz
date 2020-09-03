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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659025"
---
# <a name="initializecorrelation-activity-designer"></a>Návrhář aktivity InitializeCorrelation
Návrhář aktivity **InitializeCorrelation** slouží k vytvoření a konfiguraci <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity, která se používá k navázání korelace mezi zprávami před jejich odesláním nebo přijetím.

## <a name="the-initializecorrelation-activity"></a>Aktivita InitializeCorrelation
 <xref:System.ServiceModel.Activities.InitializeCorrelation>Aktivita se používá k inicializaci korelací bez odeslání nebo přijetí zprávy. Při odesílání nebo přijímání zprávy se obvykle inicializuje korelace. Pokud musí být korelační zpráva navázána před odesláním nebo přijetím zprávy, použijte <xref:System.ServiceModel.Activities.InitializeCorrelation> k inicializaci korelace.

### <a name="using-the-initializecorrelation-activity-designer"></a>Pomocí návrháře aktivity InitializeCorrelation
 Návrhář aktivity **InitializeCorrelation** se dá najít v kategorii **zasílání zpráv** na **panelu nástrojů**, ke které se dostanete tak, že kliknete na kartu **panel nástrojů** na panelu nástrojů [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář aktivity **InitializeCorrelation** lze přetáhnout ze **sady nástrojů** a přetáhnout na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrch. Tím se vytvoří <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation. může se <xref:System.Activities.Activity.DisplayName%2A> Upravit v hlavičce návrháře aktivity **InitializeCorrelation** nebo v poli **DisplayName** v okně **vlastnosti** .

 <xref:System.ServiceModel.Activities.CorrelationHandle>Lze určit v poli **korelace** v okně **vlastnosti** na ploše návrháře aktivity **InitializeCorrelation** .

 Kliknutí na tlačítko se třemi tečkami vedle pole **CorrelationData** v okně **vlastnosti** nebo zobrazení... text nápovědy na ploše návrháře aktivit **InitializeCorrelation** zobrazuje dialogové okno **inicializovat korelaci** , ve kterém můžete zadat popisovač korelace a páry klíč-hodnota používané k jeho inicializaci. [!INCLUDE[crabout](../includes/crabout-md.md)] pomocí tohoto dialogového okna se v [dialogovém okně Editor kolekcí typů](../workflow-designer/type-collection-editor-dialog-box.md) zobrazí téma.

### <a name="the-initializecorrelation-properties"></a>Vlastnosti InitializeCorrelation
 V následující tabulce jsou uvedeny <xref:System.ServiceModel.Activities.InitializeCorrelation> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v okně **vlastnosti** nebo na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity Výchozí hodnota je InitializeCorrelation.<br /><br /> I když použití jiné než výchozí hodnoty pro popis není <xref:System.Activities.Activity.DisplayName%2A> bezpodmínečně nutné, jedná se o osvědčený postup pro použití takové hodnoty.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|Ne|<xref:System.ServiceModel.Activities.CorrelationHandle>Slouží k přidružení aktivit pracovního postupu v korelaci.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|Ne|Slovník dat korelace, který se týká zpráv instance pracovního postupu.<br /><br /> Pomocí dialogového okna **inicializovat korelaci** můžete nakonfigurovat <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . [!INCLUDE[crabout](../includes/crabout-md.md)] Toto dialogové okno slouží k zobrazení [dialogového okna Editor kolekcí typů](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Viz také
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)