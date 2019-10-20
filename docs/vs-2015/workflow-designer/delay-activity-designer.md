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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656801"
---
# <a name="delay-activity-designer"></a>Návrhář aktivity Delay
Návrhář aktivity **zpoždění** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.Delay>.

## <a name="the-delay-activity"></a>Aktivita zpoždění
 Aktivita <xref:System.Activities.Statements.Delay> zpozdí spuštění pracovního postupu po zadanou dobu.

### <a name="using-the-delay-activity-designer"></a>Pomocí návrháře aktivity zpoždění
 Návrhář aktivity **zpoždění** lze najít v kategorii **primitivních** prvků sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X.)

 Návrhář aktivity **zpoždění** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.Delay> s výchozím <xref:System.Activities.Activity.DisplayName%2A> zpoždění. @No__t_0 lze upravit v hlavičce návrháře aktivit **zpoždění** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-delay-properties"></a>Vlastnosti zpoždění
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.Delay> a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravit v mřížce vlastností a některé z nich je možné upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer ploše.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.Delay>. Výchozí hodnota je Delay. I když hodnota <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Podmínka|Doba, po kterou má být pracovní postup zpožděn. Tato vlastnost je nastavena v mřížce vlastností. Zadejte buď literál <xref:System.TimeSpan> ve formátu 00:00:00 nebo výraz Visual Basic pro určení množství času.|

## <a name="see-also"></a>Viz také
 [Primitivní prvky](../workflow-designer/primitives-activity-designers.md) [přiřazovat](../workflow-designer/assign-activity-designer.md) [zpoždění aktivity – Návrhář – k aktivitě](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)