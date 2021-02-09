---
title: Návrhář postupu provádění – Návrhář aktivity zpoždění
description: Přečtěte si o aktivitách zpoždění a o tom, jak můžete pomocí návrháře aktivity zpoždění vytvořit a nakonfigurovat aktivitu zpoždění.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b661dddf6c07bca34e5ea044fd1338da68f4e19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894306"
---
# <a name="delay-activity-designer"></a>Návrhář aktivity Delay

Návrhář aktivity **zpoždění** se používá k vytvoření a konfiguraci <xref:System.Activities.Statements.Delay> aktivity.

## <a name="the-delay-activity"></a>Aktivita zpoždění

<xref:System.Activities.Statements.Delay>Aktivita zpozdí provádění pracovního postupu po zadanou dobu.

### <a name="use-the-delay-activity-designer"></a>Použití návrháře aktivit zpoždění

Návrhář aktivity **zpoždění** lze najít v kategorii **primitivních** prvků sady **nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL** + **+** + **X**.

Návrhář aktivity **zpoždění** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Vyřazení návrháře aktivit vytvoří <xref:System.Activities.Statements.Delay> aktivitu s výchozí hodnotou <xref:System.Activities.Activity.DisplayName%2A> zpoždění. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře **zpoždění** aktivity nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-delay-properties"></a>Vlastnosti zpoždění

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Delay> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé z nich lze upravovat na Návrhář postupu provádění ploše.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.Delay> aktivity Výchozí hodnota je Delay. I když <xref:System.Activities.Activity.DisplayName%2A> hodnota není naprosto nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Ano|Doba, po kterou má být pracovní postup zpožděn. Tato vlastnost je nastavena v mřížce vlastností. Zadejte buď literál <xref:System.TimeSpan> ve formátu 00:00:00, nebo výraz Visual Basic a určete tak dobu.|

## <a name="see-also"></a>Viz také

- [Primitiva](../workflow-designer/primitives-activity-designers.md)
- [Řadit](../workflow-designer/assign-activity-designer.md)
- [Návrhář aktivity Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)