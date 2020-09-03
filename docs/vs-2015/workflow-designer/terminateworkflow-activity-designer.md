---
title: Návrhář aktivity TerminateWorkflow | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c204c14818a9c6e6fb0a46e6234b550838f3b1a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72607098"
---
# <a name="terminateworkflow-activity-designer"></a>Návrhář aktivity TerminateWorkflow
Návrhář aktivity **TerminateWorkflow** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.TerminateWorkflow> aktivity.

## <a name="the-terminateworkflow-activity"></a>Aktivita TerminateWorkflow
 <xref:System.Activities.Statements.TerminateWorkflow>Aktivita ukončí provádění pracovního postupu.

### <a name="using-the-terminateworkflow-activity-designer"></a>Pomocí návrháře aktivity TerminateWorkflow
 Návrhář aktivity **TerminateWorkflow** lze najít v kategorii **runtime** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panel** nástrojů (případně můžete vybrat možnost **Sada nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář aktivity **TerminateWorkflow** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.TerminateWorkflow> aktivita s výchozím **názvem DisplayName** TerminateWorkflow. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře aktivity **TerminateWorkflow** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-terminateworkflow-properties"></a>Vlastnosti TerminateWorkflow
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.TerminateWorkflow> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností a některé z nich je možné upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.TerminateWorkflow> aktivity Výchozí hodnota je TerminateWorkflow. I když zobrazovaný název není nezbytně nutný, je vhodné použít zobrazovaný název.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|Ne|Výjimka, která se má vyvolat při ukončení pracovního postupu. Tuto vlastnost nastavte v mřížce vlastností.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|Ne|Důvod vysvětlení, proč byl pracovní postup ukončen. Tuto vlastnost nastavte v mřížce vlastností.|

## <a name="see-also"></a>Viz také
 [Doba běhu](../workflow-designer/runtime-activity-designers.md) – [zachování](../workflow-designer/persist-activity-designer.md)