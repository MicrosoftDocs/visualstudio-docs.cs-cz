---
title: Návrhář aktivity Návrhář postupu provádění – CorrelationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 135acfbbaf9fdcbbf219fd50a504cf9262fe4d24
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876096"
---
# <a name="correlationscope-activity-designer"></a>Návrhář aktivity CorrelationScope

Návrhář aktivity **CorrelationScope** slouží k vytvoření a konfiguraci <xref:System.ServiceModel.Activities.CorrelationScope> aktivity, která poskytuje implicitní správu podřízených aktivit zasílání zpráv pomocí <xref:System.ServiceModel.Activities.CorrelationHandle> objektu.

## <a name="the-correlationscope-activity"></a>Aktivita CorrelationScope

<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>Vlastnost určuje, která se <xref:System.ServiceModel.Activities.CorrelationHandle> používá ke správě aktivit podřízeného zasílání zpráv. <xref:System.ServiceModel.Activities.Send>Aktivity a <xref:System.ServiceModel.Activities.Receive> obsažené v <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> jsou nakonfigurovány tak, aby používaly <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> vlastnost obsahující <xref:System.ServiceModel.Activities.CorrelationScope> aktivity k provedení korelace.

### <a name="use-the-correlationscope-activity-designer"></a>Použití návrháře aktivity CorrelationScope

Návrhář aktivity **CorrelationScope** se dá najít v kategorii **zasílání zpráv** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** + **+** + **X**.

Návrhář aktivity **CorrelationScope** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu. Tím se vytvoří <xref:System.ServiceModel.Activities.CorrelationScope> aktivita s výchozím **názvem DisplayName** CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v hlavičce návrháře aktivity **CorrelationScope** nebo v poli **DisplayName** v okně **vlastnosti** .

Chcete-li určit <xref:System.ServiceModel.Activities.CorrelationHandle> používané aktivity podřízeného zasílání zpráv, vyberte tlačítko se třemi tečkami vedle pole **popisovač CorrelatesWith** v okně **vlastnosti** . zobrazí se dialogové okno **Editor výrazů** . Tuto vlastnost lze také nastavit na ploše návrháře aktivit.

Aktivity v oboru v rámci korelace jsou určeny tak, že se jejich návrháři vyřadí do pole **text** v rámci **CorrelationScope** designeru.

### <a name="the-correlationscope-properties"></a>Vlastnosti CorrelationScope

V následující tabulce jsou uvedeny <xref:System.ServiceModel.Activities.CorrelationScope> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit buď v okně **vlastnosti** , nebo na Návrhář postupu provádění povrchu a často v obou.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Volitelný popisný název <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Ne|Určuje, který se <xref:System.ServiceModel.Activities.CorrelationHandle> používá ke správě aktivit podřízeného zasílání zpráv. Pokud tuto vlastnost nenastavíte, <xref:System.ServiceModel.Activities.CorrelationScope> vytvoří implicitní automatické vytváření <xref:System.ServiceModel.Activities.CorrelationHandle> .|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Ne|Určuje aktivity v oboru korelace.|

## <a name="see-also"></a>Viz také

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Přijmout](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Odeslat](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)