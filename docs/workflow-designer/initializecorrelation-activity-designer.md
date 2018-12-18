---
title: Návrhář postupu provádění – Návrhář aktivity Initializecorrelation
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f72cb538018588ab11335be5a99fe86b5c474c3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879880"
---
# <a name="initializecorrelation-activity-designer"></a>Návrhář aktivity InitializeCorrelation

**InitializeCorrelation** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity. <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivita vytváří korelaci mezi zprávy před odesláním nebo jejich přijetí.

## <a name="the-initializecorrelation-activity"></a>Aktivity InitializeCorrelation

<xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivita slouží k inicializaci korelace bez odesílání nebo přijímání zprávy. Korelace je obvykle inicializován při odesílání nebo přijímání zprávy. Pokud korelace musí vytvořit předtím, než je odeslání nebo přijetí zprávy, použijte <xref:System.ServiceModel.Activities.InitializeCorrelation> inicializace korelace.

### <a name="using-the-initializecorrelation-activity-designer"></a>Pomocí aktivity Initializecorrelation

Přístup **InitializeCorrelation** návrháře aktivit v **zasílání zpráv** kategorii **nástrojů**.

**InitializeCorrelation** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění. Vyřazení Návrhář aktivity vytvoří <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity s výchozím <xref:System.Activities.Activity.DisplayName%2A> z InitializeCorrelation. <xref:System.Activities.Activity.DisplayName%2A> Můžete upravovat v záhlaví **InitializeCorrelation** Návrhář aktivity nebo **DisplayName** pomocí boxingu **vlastnosti** okno.

<xref:System.ServiceModel.Activities.CorrelationHandle> Může být určuje v **korelace** pole **vlastnosti** na okno **InitializeCorrelation** povrch návrháře aktivit.

Chcete-li zobrazit **inicializace korelace** dialogovému oknu, kde můžete zadat popisovač korelace a páry klíč hodnota použitý k inicializaci, vyberte tlačítko se třemi tečkami vedle **initalizecorrelation CorrelationData** pole v **vlastnosti** okna. Nebo vyberte text nápovědy "Zobrazit …" na **InitializeCorrelation** povrch návrháře aktivit. Další informace o tomto dialogovém okně najdete v článku [dialogové okno Editor typu kolekce](../workflow-designer/type-collection-editor-dialog-box.md) článku.

### <a name="the-initializecorrelation-properties"></a>Vlastnosti InitializeCorrelation

Následující tabulka ukazuje <xref:System.ServiceModel.Activities.InitializeCorrelation> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravovat v **vlastnosti** okně nebo na plochu návrháře postupu provádění.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity. Výchozí hodnota je InitializeCorrelation.<br /><br /> Ačkoli použití jinou než výchozí hodnotu pro popisný <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, doporučujeme.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> Použito k přidružení pracovního postupu aktivit v korelaci.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Slovník korelace dat, které se týkají zprávy instance pracovního postupu.<br /><br /> Použití **inicializace korelace** dialogové okno Konfigurace <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Další informace o použití tomto dialogovém okně najdete v článku [dialogové okno Editor typu kolekce](../workflow-designer/type-collection-editor-dialog-box.md) článku.|

## <a name="see-also"></a>Viz také:

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)