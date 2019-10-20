---
title: InvokeDelegate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc35aec714255b467431488936605fb37009db9d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659008"
---
# <a name="invokedelegate"></a>InvokeDelegate

Návrhář **InvokeDelegate** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.InvokeDelegate>.

## <a name="the-invokedelegate-activity"></a>Aktivita InvokeDelegate

@No__t_0 volá veřejný delegát.

### <a name="using-the-invokedelegate-activity-designer"></a>Pomocí návrháře aktivity InvokeDelegate

Návrhář aktivity **InvokeDelegate** lze najít v kategorii **primitivních** prvků sady **nástrojů**, ke které se dostanete kliknutím na kartu **panel nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CRTL + ALT + X.)

Návrhář aktivity **InvokeDelegate** lze přetáhnout ze **sady nástrojů** a přetáhnout na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.InvokeDelegate> s výchozím <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. @No__t_0 lze upravit v hlavičce návrháře aktivity **InvokeDelegate** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-invokedelegate-properties"></a>Vlastnosti InvokeDelegate

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.InvokeDelegate> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé mohou být upravovány na [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer povrchu.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.InvokeDelegate>. Výchozí hodnota je InvokeDelegate.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Podmínka|Název <xref:System.Activities.ActivityDelegate>, který se má volat, když se aktivita spustí Tato vlastnost se dá upravit na návrhové ploše. Toto je povinná vlastnost.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Kolekce argumentů volaného delegáta. Klíče jsou názvy <xref:System.Activities.DelegateArgument> objektů v <xref:System.Activities.ActivityDelegate> a hodnoty jsou argumenty, jejichž výrazy jsou vyhodnocovány a přiřazeny odpovídajícím objektům <xref:System.Activities.DelegateArgument>. V mřížce vlastností klikněte na tlačítko se třemi tečkami v poli **DelegateArguments** , zobrazí se dialogové okno **DelegateArguments** , které vám umožní nastavit tuto vlastnost. Klikněte na pole **vytvořit argument** a přidejte argumenty.|

## <a name="see-also"></a>Viz také:

- [Postupy: Definování a použití delegátů aktivit v návrháři postupu provádění](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)