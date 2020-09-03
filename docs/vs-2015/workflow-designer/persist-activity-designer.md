---
title: Návrhář aktivity trvalého uložení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60a63dd4036863641646e85a89f5018cba786802
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672628"
---
# <a name="persist-activity-designer"></a>Návrhář aktivity Persist
Návrhář **trvalé** aktivity se používá k vytvoření a konfiguraci <xref:System.Activities.Statements.Persist> aktivity.

## <a name="the-persist-activity"></a>Aktivita trvalosti
 <xref:System.Activities.Statements.Persist>Pokud je to možné, aktivita ukládá pracovní postup na disk. <xref:System.Activities.Statements.Persist>Aktivitu nelze provést v zóně bez trvalého uložení, například v rámci <xref:System.Activities.Statements.TransactionScope> aktivity. Pokud použijete <xref:System.Activities.Statements.Persist> aktivitu v oboru, který není trvalý, výjimka je vyvolána za běhu.

### <a name="using-the-persist-activity-designer"></a>Použití návrháře trvalé aktivity
 Návrháře **trvalých** aktivit lze najít v kategorii **runtime** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panel** nástrojů (případně můžete vybrat možnost **Sada nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).)

 Návrháře **trvalé** aktivity lze přetáhnout ze **sady nástrojů** a umístit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.Persist> aktivita s výchozím **názvem DisplayName** trvalého. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře **trvalé** aktivity nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-persist-properties"></a>Trvalé vlastnosti
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Persist> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností a některé z nich je možné upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.Persist> aktivity Výchozí hodnota je trvalá. I když zobrazovaný název není nezbytně nutný, je vhodné použít zobrazovaný název.|

## <a name="see-also"></a>Viz také
 [Běhové](../workflow-designer/runtime-activity-designers.md) [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)