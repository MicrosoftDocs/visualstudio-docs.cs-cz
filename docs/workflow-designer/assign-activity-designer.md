---
title: Návrhář aktivity Návrhář postupu provádění – přiřazení
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44d4136aabd5bd383cc3718dc5c6c1676f94e45d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650733"
---
# <a name="assign-activity-designer"></a>Návrhář aktivity Assign

Návrhář **přiřazení** aktivity se používá k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.Assign>.

## <a name="the-assign-activity"></a>Aktivita přiřazení

Aktivita <xref:System.Activities.Statements.Assign> přiřadí hodnotu proměnné nebo argumentu.

### <a name="using-the-assign-activity-designer"></a>Použití návrháře přiřazení aktivity

Návrháře **přiřazení** aktivity lze najít v kategorii **primitivních** prvků sady **nástrojů**, ke které se dostanete kliknutím na kartu **panel** nástrojů (případně můžete vybrat možnost **Sada nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).)

Návrháře **přiřazení** aktivity lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu, kde jsou umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Vyřazením návrháře aktivity pro **přiřazení** dojde k vytvoření aktivity <xref:System.Activities.Statements.Assign> s výchozím názvem **DisplayName** (přiřadit). @No__t_0 lze upravit v hlavičce návrháře aktivity **přiřazení** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-assign-properties"></a>Vlastnosti přiřazení

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.Assign> a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností a některé z nich je možné upravovat na Návrhář postupu provádění povrchu.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.Assign>. Výchozí hodnota je přiřazení. I když hodnota <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutná, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.Assign.To%2A>|Podmínka|Proměnná nebo argument, ke kterému je přiřazena <xref:System.Activities.Statements.Assign.Value%2A>. Hodnota musí být platným identifikátorem Visual Basic. Chcete-li nastavit vlastnost, zadejte výraz Visual Basic do pole **do** v Návrháři **přiřazení** aktivity nebo v mřížce vlastností.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Podmínka|Hodnota, která je přiřazena proměnné. Chcete-li nastavit <xref:System.Activities.Statements.Assign.Value%2A>, zadejte výraz Visual Basic do pole **hodnota** v Návrháři **přiřazení** aktivity nebo v mřížce vlastností.|

## <a name="see-also"></a>Viz také:

- [Primitivní elementy](../workflow-designer/primitives-activity-designers.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)