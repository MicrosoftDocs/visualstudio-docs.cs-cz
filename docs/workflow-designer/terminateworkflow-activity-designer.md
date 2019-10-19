---
title: Návrhář aktivity Návrhář postupu provádění – TerminateWorkflow
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01003005e9f73138e5a430b21e538c5c241e7f9f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649886"
---
# <a name="terminateworkflow-activity-designer"></a>Návrhář aktivity TerminateWorkflow

Návrhář aktivity **TerminateWorkflow** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.TerminateWorkflow>.

## <a name="the-terminateworkflow-activity"></a>Aktivita TerminateWorkflow

Aktivita <xref:System.Activities.Statements.TerminateWorkflow> ukončí provádění pracovního postupu.

### <a name="using-the-terminateworkflow-activity-designer"></a>Pomocí návrháře aktivity TerminateWorkflow

Návrhář aktivity **TerminateWorkflow** lze najít v kategorii **runtime** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panel** nástrojů (případně můžete vybrat **panel nástrojů** v nabídce zobrazení nebo CTRL + ALT +) **.** X.)

Návrhář aktivity **TerminateWorkflow** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.TerminateWorkflow> s výchozím **názvem DisplayName** TerminateWorkflow. @No__t_0 lze upravit v hlavičce návrháře aktivity **TerminateWorkflow** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-terminateworkflow-properties"></a>Vlastnosti TerminateWorkflow

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.TerminateWorkflow> a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností a některé z nich je možné upravovat na Návrhář postupu provádění povrchu.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.TerminateWorkflow>. Výchozí hodnota je TerminateWorkflow. I když zobrazovaný název není nezbytně nutný, je vhodné použít zobrazovaný název.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Výjimka, která se má vyvolat při ukončení pracovního postupu. Tuto vlastnost nastavte v mřížce vlastností.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Důvod vysvětlení, proč byl pracovní postup ukončen. Tuto vlastnost nastavte v mřížce vlastností.|

## <a name="see-also"></a>Viz také:

- [Modul runtime](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)