---
title: Přiřadit návrháře aktivit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ebe465d5eeb12a956d285a8313b0acdbcfb8d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659191"
---
# <a name="assign-activity-designer"></a>Návrhář aktivity Assign
Návrhář **přiřazení** aktivity se používá k vytvoření a konfiguraci <xref:System.Activities.Statements.Assign> aktivity.

## <a name="the-assign-activity"></a>Aktivita přiřazení
 <xref:System.Activities.Statements.Assign>Aktivita přiřadí hodnotu proměnné nebo argumentu.

### <a name="using-the-assign-activity-designer"></a>Použití návrháře přiřazení aktivity
 Návrháře **přiřazení** aktivity lze najít v kategorii **primitivních** prvků sady **nástrojů**, ke které se dostanete kliknutím na kartu **panel** nástrojů (případně můžete vybrat možnost **Sada nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).)

 Návrháře **přiřazení** aktivity lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.Assign> aktivita s výchozím **zobrazovaným názvem** pro přiřazení. Je <xref:System.Activities.Activity.DisplayName%2A> možné upravit v záhlaví návrháře aktivity **přiřazení** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-assign-properties"></a>Vlastnosti přiřazení
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Assign> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností a některé z nich je možné upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.Assign> aktivity Výchozí hodnota je přiřazení. I když není <xref:System.Activities.Activity.DisplayName%2A> hodnota striktně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.Assign.To%2A>|Ano|Proměnná nebo argument, ke kterému <xref:System.Activities.Statements.Assign.Value%2A> je přiřazena. Musí to být platný identifikátor Visual Basic. Chcete-li nastavit vlastnost, zadejte výraz Visual Basic do pole **do** v Návrháři **přiřazení** aktivity nebo v mřížce vlastností.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Ano|Hodnota, která je přiřazena proměnné. Chcete-li nastavit <xref:System.Activities.Statements.Assign.Value%2A> , zadejte výraz Visual Basic do pole **hodnota** v Návrháři **přiřazení** aktivity nebo v mřížce vlastností.|

## <a name="see-also"></a>Viz také
 Zpoždění [primitiv](../workflow-designer/primitives-activity-designers.md) – [zpožděna](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) – [WriteLine](../workflow-designer/writeline-activity-designer.md)