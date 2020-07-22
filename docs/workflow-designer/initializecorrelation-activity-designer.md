---
title: Návrhář aktivity Návrhář postupu provádění – InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aadb526e50351c8344c8b265dca3364637d1ff0c
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875563"
---
# <a name="initializecorrelation-activity-designer"></a>Návrhář aktivity InitializeCorrelation

Návrhář aktivity **InitializeCorrelation** slouží k vytvoření a konfiguraci <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity. Tato <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivita vytváří korelaci mezi zprávami před jejich odesláním nebo přijetím.

## <a name="the-initializecorrelation-activity"></a>Aktivita InitializeCorrelation

<xref:System.ServiceModel.Activities.InitializeCorrelation>Aktivita se používá k inicializaci korelací bez odeslání nebo přijetí zprávy. Při odesílání nebo přijímání zprávy se obvykle inicializuje korelace. Pokud musí být korelační zpráva navázána před odesláním nebo přijetím zprávy, použijte <xref:System.ServiceModel.Activities.InitializeCorrelation> k inicializaci korelace.

### <a name="using-the-initializecorrelation-activity-designer"></a>Pomocí návrháře aktivity InitializeCorrelation

Přístup k Návrháři aktivity **InitializeCorrelation** v kategorii **zasílání zpráv** sady **nástrojů**.

Návrhář aktivity **InitializeCorrelation** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu. Vyřazení návrháře aktivit vytvoří <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivitu s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v hlavičce návrháře aktivity **InitializeCorrelation** nebo v poli **DisplayName** v okně **vlastnosti** .

<xref:System.ServiceModel.Activities.CorrelationHandle>Lze určit v poli **korelace** v okně **vlastnosti** na ploše návrháře aktivity **InitializeCorrelation** .

Chcete-li zobrazit dialogové okno **inicializovat korelaci** , kde můžete zadat popisovač korelace a páry klíč-hodnota použité k jeho inicializaci, vyberte tlačítko se třemi tečkami vedle pole **CorrelationData** v okně **vlastnosti** . Nebo vyberte Zobrazit... text nápovědy na ploše návrháře aktivity **InitializeCorrelation** Další informace o používání tohoto dialogového okna naleznete v článku [dialogové okno Editor kolekcí typů](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Vlastnosti InitializeCorrelation

V následující tabulce jsou uvedeny <xref:System.ServiceModel.Activities.InitializeCorrelation> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v okně **vlastnosti** nebo na Návrhář postupu provádění ploše.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Popisný název <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity Výchozí hodnota je InitializeCorrelation.<br /><br /> I když použití jiné než výchozí hodnoty pro popis <xref:System.Activities.Activity.DisplayName%2A> není naprosto povinné, doporučuje se.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|Nepravda|<xref:System.ServiceModel.Activities.CorrelationHandle>Slouží k přidružení aktivit pracovního postupu v korelaci.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|Nepravda|Slovník dat korelace, který se týká zpráv instance pracovního postupu.<br /><br /> Pomocí dialogového okna **inicializovat korelaci** můžete nakonfigurovat <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . Další informace o tom, jak používat toto dialogové okno, najdete v článku [dialogové okno Editor kolekcí typů](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Viz také

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Přijmout](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Odeslat](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)