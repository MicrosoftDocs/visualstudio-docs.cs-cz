---
title: Návrhář aktivity zpoždění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a47279bc68503ba645fea3ef23a04ce9d5ef4c41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656801"
---
# <a name="delay-activity-designer"></a>Návrhář aktivity Delay
Návrhář aktivity **zpoždění** se používá k vytvoření a konfiguraci <xref:System.Activities.Statements.Delay> aktivity.

## <a name="the-delay-activity"></a>Aktivita zpoždění
 <xref:System.Activities.Statements.Delay>Aktivita zpozdí provádění pracovního postupu po zadanou dobu.

### <a name="using-the-delay-activity-designer"></a>Pomocí návrháře aktivity zpoždění
 Návrhář aktivity **zpoždění** lze najít v kategorii **primitivních** prvků sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář aktivity **zpoždění** lze přetáhnout ze **sady nástrojů** a [!INCLUDE[wfd2](../includes/wfd2-md.md)] umístit na plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.Delay> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> Delay. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře **zpoždění** aktivity nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-delay-properties"></a>Vlastnosti zpoždění
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Delay> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé z nich lze upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.Delay> aktivity Výchozí hodnota je Delay. I když není <xref:System.Activities.Activity.DisplayName%2A> hodnota striktně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Ano|Doba, po kterou má být pracovní postup zpožděn. Tato vlastnost je nastavena v mřížce vlastností. Zadejte buď literál <xref:System.TimeSpan> ve formátu 00:00:00, nebo výraz Visual Basic a určete tak dobu.|

## <a name="see-also"></a>Viz také
 [Primitivní prvky](../workflow-designer/primitives-activity-designers.md) [přiřazovat](../workflow-designer/assign-activity-designer.md) [zpoždění aktivity – Návrhář – k aktivitě](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)