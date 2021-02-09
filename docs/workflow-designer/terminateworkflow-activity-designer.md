---
title: Návrhář aktivity TerminateWorkflow
description: V Návrhář postupu provádění se dozvíte, jak můžete pomocí návrháře aktivit TerminateWorkflow vytvořit a nakonfigurovat aktivitu TerminateWorkflow.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3f37c862768dd0d72ba66d435478faed9bee8ef3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931484"
---
# <a name="terminateworkflow-activity-designer"></a>Návrhář aktivity TerminateWorkflow

Návrhář aktivity **TerminateWorkflow** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.TerminateWorkflow> aktivity.

## <a name="the-terminateworkflow-activity"></a>Aktivita TerminateWorkflow

<xref:System.Activities.Statements.TerminateWorkflow>Aktivita ukončí provádění pracovního postupu.

### <a name="using-the-terminateworkflow-activity-designer"></a>Pomocí návrháře aktivity TerminateWorkflow

Návrhář aktivity **TerminateWorkflow** lze najít v kategorii **runtime** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panel** nástrojů (případně můžete vybrat možnost **Sada nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

Návrhář aktivity **TerminateWorkflow** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.TerminateWorkflow> aktivita s výchozím **názvem DisplayName** TerminateWorkflow. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře aktivity **TerminateWorkflow** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-terminateworkflow-properties"></a>Vlastnosti TerminateWorkflow

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.TerminateWorkflow> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností a některé z nich je možné upravovat na Návrhář postupu provádění povrchu.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.TerminateWorkflow> aktivity Výchozí hodnota je TerminateWorkflow. I když zobrazovaný název není nezbytně nutný, je vhodné použít zobrazovaný název.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|Ne|Výjimka, která se má vyvolat při ukončení pracovního postupu. Tuto vlastnost nastavte v mřížce vlastností.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|Ne|Důvod vysvětlení, proč byl pracovní postup ukončen. Tuto vlastnost nastavte v mřížce vlastností.|

## <a name="see-also"></a>Viz také

- [Runtime (Modul runtime)](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)
