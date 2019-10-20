---
title: Návrhář aktivity Návrhář postupu provádění – CorrelationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d65e481342f7b7e86b3ce073b7d6a15254ae72d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650586"
---
# <a name="correlationscope-activity-designer"></a>Návrhář aktivity CorrelationScope

Návrhář aktivity **CorrelationScope** slouží k vytvoření a konfiguraci aktivity <xref:System.ServiceModel.Activities.CorrelationScope>, která poskytuje implicitní správu aktivit podřízeného zasílání zpráv pomocí objektu <xref:System.ServiceModel.Activities.CorrelationHandle>.

## <a name="the-correlationscope-activity"></a>Aktivita CorrelationScope

Vlastnost <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> určuje <xref:System.ServiceModel.Activities.CorrelationHandle>, která se používá ke správě podřízených aktivit zasílání zpráv. Aktivity <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> obsažené v <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> jsou nakonfigurovány tak, aby pro provádění korelace používaly vlastnost <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> aktivity obsahující <xref:System.ServiceModel.Activities.CorrelationScope>.

### <a name="use-the-correlationscope-activity-designer"></a>Použití návrháře aktivity CorrelationScope

Návrhář aktivity **CorrelationScope** se dá najít v kategorii **zasílání zpráv** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** +**ALT** +**X**.

Návrhář aktivity **CorrelationScope** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu. Tím se vytvoří aktivita <xref:System.ServiceModel.Activities.CorrelationScope> s výchozím **názvem DisplayName** CorrelationScope. @No__t_0 lze upravit v hlavičce návrháře aktivity **CorrelationScope** nebo v poli **DisplayName** v okně **vlastnosti** .

Chcete-li určit <xref:System.ServiceModel.Activities.CorrelationHandle> používané aktivitami podřízeného zasílání zpráv, vyberte tlačítko se třemi tečkami vedle pole **popisovač CorrelatesWith** v okně **vlastnosti** a zobrazte tak dialogové okno **Editor výrazů** . Tuto vlastnost lze také nastavit na ploše návrháře aktivit.

Aktivity v oboru v rámci korelace jsou určeny tak, že se jejich návrháři vyřadí do pole **text** v rámci **CorrelationScope** designeru.

### <a name="the-correlationscope-properties"></a>Vlastnosti CorrelationScope

V následující tabulce jsou uvedeny vlastnosti <xref:System.ServiceModel.Activities.CorrelationScope> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit buď v okně **vlastnosti** , nebo na Návrhář postupu provádění povrchu a často v obou.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Volitelný popisný název aktivity <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Určuje <xref:System.ServiceModel.Activities.CorrelationHandle> pro správu aktivit podřízeného zasílání zpráv. Pokud tuto vlastnost nenastavíte, <xref:System.ServiceModel.Activities.CorrelationScope> automaticky vytvoří implicitní <xref:System.ServiceModel.Activities.CorrelationHandle>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Určuje aktivity v oboru korelace.|

## <a name="see-also"></a>Viz také:

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)