---
title: Návrhář postupu provádění – Návrhář aktivity zpoždění
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5190807bba08f05e176acc15ac8daf42ac028c50
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650551"
---
# <a name="delay-activity-designer"></a>Návrhář aktivity Delay

Návrhář aktivity **zpoždění** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.Delay>.

## <a name="the-delay-activity"></a>Aktivita zpoždění

Aktivita <xref:System.Activities.Statements.Delay> zpozdí spuštění pracovního postupu po zadanou dobu.

### <a name="use-the-delay-activity-designer"></a>Použití návrháře aktivit zpoždění

Návrhář aktivity **zpoždění** lze najít v kategorii **primitivních** prvků sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** +**ALT** +**X**.

Návrhář aktivity **zpoždění** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Vyřazení návrháře aktivit vytvoří aktivitu <xref:System.Activities.Statements.Delay> s výchozím <xref:System.Activities.Activity.DisplayName%2A> zpoždění. @No__t_0 lze upravit v hlavičce návrháře aktivit **zpoždění** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-delay-properties"></a>Vlastnosti zpoždění

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.Delay> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé z nich lze upravovat na Návrhář postupu provádění ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.Delay>. Výchozí hodnota je Delay. I když hodnota <xref:System.Activities.Activity.DisplayName%2A> není striktně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Podmínka|Doba, po kterou má být pracovní postup zpožděn. Tato vlastnost je nastavena v mřížce vlastností. Zadejte buď literál <xref:System.TimeSpan> ve formátu 00:00:00 nebo výraz Visual Basic pro určení množství času.|

## <a name="see-also"></a>Viz také:

- [Primitivní elementy](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Návrhář aktivity Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)