---
title: Návrhář postupu provádění – InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 5227d96e3fad03dd3e3309523a6d2c68a1abdc11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650184"
---
# <a name="invokedelegate"></a>InvokeDelegate

Návrhář **InvokeDelegate** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.InvokeDelegate>.

## <a name="the-invokedelegate-activity"></a>Aktivita InvokeDelegate

@No__t_0 volá veřejný delegát.

### <a name="use-the-invokedelegate-activity-designer"></a>Použití návrháře aktivity InvokeDelegate

Přístup k Návrháři aktivity **InvokeDelegate** v kategorii **primitivních** prvků sady **nástrojů** Návrhář aktivity **InvokeDelegate** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Vyřazení návrháře aktivit vytvoří aktivitu <xref:System.Activities.Statements.InvokeDelegate> s výchozím <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. @No__t_0 lze upravit v hlavičce návrháře aktivity **InvokeDelegate** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-invokedelegate-properties"></a>Vlastnosti InvokeDelegate

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.InvokeDelegate> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností a některé lze upravovat na Návrhář postupu provádění ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.InvokeDelegate>. Výchozí hodnota je InvokeDelegate.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je vhodné použít jeden.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Podmínka|Název <xref:System.Activities.ActivityDelegate>, který se má volat, když se aktivita spustí Tato vlastnost se dá upravovat na návrhové ploše a je povinná.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Kolekce argumentů volaného delegáta. Klíče jsou názvy objektů parametrů na <xref:System.Activities.ActivityDelegate> a hodnoty jsou argumenty, jejichž výrazy jsou vyhodnocovány a přiřazeny odpovídajícím objektům parametrů. Chcete-li zobrazit dialogové okno **DelegateArguments** , kde můžete nastavit tuto vlastnost, klikněte na tlačítko se třemi tečkami v poli **DelegateArguments** v mřížce vlastností. Klikněte na pole **vytvořit argument** a přidejte argumenty.|

## <a name="see-also"></a>Viz také:

- [Postupy: Definování a použití delegátů aktivit v návrháři postupu provádění](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)