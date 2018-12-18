---
title: Návrhář postupu provádění – Návrhář aktivity Correlationscope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d1da881dfb7f7a8c063b94e49198d1b299b2e47b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942046"
---
# <a name="correlationscope-activity-designer"></a>Návrhář aktivity CorrelationScope

**CorrelationScope** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.ServiceModel.Activities.CorrelationScope> aktivitu, která poskytuje implicitní správu podřízených aktivit zasílání zpráv pomocí <xref:System.ServiceModel.Activities.CorrelationHandle> objektu.

## <a name="the-correlationscope-activity"></a>Aktivity CorrelationScope

<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> Určuje vlastnost <xref:System.ServiceModel.Activities.CorrelationHandle> používá ke správě podřízených aktivit zasílání zpráv. <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> aktivity obsažené v <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> jsou nakonfigurovány pro použití <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> vlastnosti nadřazeného <xref:System.ServiceModel.Activities.CorrelationScope> aktivita k provedení korelace.

### <a name="use-the-correlationscope-activity-designer"></a>Použití aktivity Correlationscope

**CorrelationScope** návrháře aktivit najdete v **zasílání zpráv** kategorii **nástrojů**, který přistupuje po kliknutí **nástrojů** karty na levé straně návrháře postupu provádění. Můžete také vybrat **nástrojů** z **zobrazení** nabídky nebo stisknutím klávesy **Ctrl**+**Alt** + **X**.

**CorrelationScope** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění. Tím se vytvoří <xref:System.ServiceModel.Activities.CorrelationScope> aktivity s výchozím **DisplayName** z CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A> Můžete upravovat v záhlaví **CorrelationScope** Návrhář aktivity nebo **DisplayName** pomocí boxingu **vlastnosti** okno.

Chcete-li určit <xref:System.ServiceModel.Activities.CorrelationHandle> používají podřízené aktivity zasílání zpráv, vyberte tlačítko se třemi tečkami vedle **CorrelatesWith** pole v **vlastnosti** okno k zobrazení **výraz Editor** dialogové okno. Tuto vlastnost můžete také nastavit na plochu návrháře aktivit.

Aktivity s rozsahem v rámci korelace jsou určeny umístěním jejich návrháře v rámci **tělo** pole v rámci **CorrelationScope** návrháře.

### <a name="the-correlationscope-properties"></a>Vlastnosti CorrelationScope

Následující tabulka ukazuje <xref:System.ServiceModel.Activities.CorrelationScope> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v **vlastnosti** okně nebo na povrchu návrháře postupu provádění a často v obou.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Volitelné jméno <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Určuje, <xref:System.ServiceModel.Activities.CorrelationHandle> používá ke správě podřízených aktivit zasílání zpráv. Pokud tuto vlastnost nenastavíte <xref:System.ServiceModel.Activities.CorrelationScope> vytvoří implicitní <xref:System.ServiceModel.Activities.CorrelationHandle> automaticky.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Určuje aktivity v rámci rozsahu korelace.|

## <a name="see-also"></a>Viz také:

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)