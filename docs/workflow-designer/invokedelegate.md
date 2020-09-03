---
title: Návrhář postupu provádění – InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
author: TerryGLee
ms.author: tglee
ms.workload:
- multiple
ms.openlocfilehash: 9e63fb7a766b79467749cc5181a575e0d35a07b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876070"
---
# <a name="invokedelegate"></a>InvokeDelegate

Návrhář **InvokeDelegate** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.InvokeDelegate> aktivity.

## <a name="the-invokedelegate-activity"></a>Aktivita InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate>Volá veřejného delegáta.

### <a name="use-the-invokedelegate-activity-designer"></a>Použití návrháře aktivity InvokeDelegate

Přístup k Návrháři aktivity **InvokeDelegate** v kategorii **primitivních** prvků sady **nástrojů** Návrhář aktivity **InvokeDelegate** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Vyřazení návrháře aktivit vytvoří <xref:System.Activities.Statements.InvokeDelegate> aktivitu s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře aktivity **InvokeDelegate** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-invokedelegate-properties"></a>Vlastnosti InvokeDelegate

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.InvokeDelegate> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností a některé lze upravovat na Návrhář postupu provádění ploše.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.InvokeDelegate> aktivity Výchozí hodnota je InvokeDelegate.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je vhodné použít jeden.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Ano|Název, který se má <xref:System.Activities.ActivityDelegate> volat, když se aktivita spustí. Tato vlastnost se dá upravovat na návrhové ploše a je povinná.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Ne|Kolekce argumentů volaného delegáta. Klíče jsou názvy objektů parametrů v a <xref:System.Activities.ActivityDelegate> hodnoty jsou argumenty, jejichž výrazy jsou vyhodnocovány a přiřazeny odpovídajícím objektům parametrů. Chcete-li zobrazit dialogové okno **DelegateArguments** , kde můžete nastavit tuto vlastnost, klikněte na tlačítko se třemi tečkami v poli **DelegateArguments** v mřížce vlastností. Klikněte na pole **vytvořit argument** a přidejte argumenty.|

## <a name="see-also"></a>Viz také

- [Postupy: Definování a použití delegátů aktivit v návrháři postupu provádění](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)