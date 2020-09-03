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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659008"
---
# <a name="invokedelegate"></a>InvokeDelegate

Návrhář **InvokeDelegate** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.InvokeDelegate> aktivity.

## <a name="the-invokedelegate-activity"></a>Aktivita InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate>Volá veřejného delegáta.

### <a name="using-the-invokedelegate-activity-designer"></a>Pomocí návrháře aktivity InvokeDelegate

Návrhář aktivity **InvokeDelegate** lze najít v kategorii **primitivních** prvků na **panelu nástrojů**, ke kterému se dostanete kliknutím **na kartu panel nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CRTL + ALT + X).)

Návrhář aktivity **InvokeDelegate** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.InvokeDelegate> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře aktivity **InvokeDelegate** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-invokedelegate-properties"></a>Vlastnosti InvokeDelegate

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.InvokeDelegate> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé lze upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.InvokeDelegate> aktivity Výchozí hodnota je InvokeDelegate.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Ano|Název, který se má <xref:System.Activities.ActivityDelegate> volat, když se aktivita spustí. Tato vlastnost se dá upravit na návrhové ploše. Toto je povinná vlastnost.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Ne|Kolekce argumentů volaného delegáta. Klíče jsou názvy <xref:System.Activities.DelegateArgument> objektů na <xref:System.Activities.ActivityDelegate> a hodnoty jsou argumenty, jejichž výrazy jsou vyhodnocovány a přiřazeny odpovídajícím <xref:System.Activities.DelegateArgument> objektům. V mřížce vlastností klikněte na tlačítko se třemi tečkami v poli **DelegateArguments** , zobrazí se dialogové okno **DelegateArguments** , které vám umožní nastavit tuto vlastnost. Klikněte na pole **vytvořit argument** a přidejte argumenty.|

## <a name="see-also"></a>Viz také

- [Postupy: Definování a použití delegátů aktivit v návrháři postupu provádění](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)