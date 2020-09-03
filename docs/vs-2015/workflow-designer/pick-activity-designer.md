---
title: Návrhář aktivity výběru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: daefc48cfff2c5c73d9ecf14316777becf4d83c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672600"
---
# <a name="pick-activity-designer"></a>Návrhář aktivity Pick
<xref:System.Activities.Statements.Pick>Aktivita poskytuje tok řízení založený na událostech. Aktivita spustí jednu z několika větví v reakci na událost triggeru.

## <a name="the-pick-activity"></a>Aktivita výběru
 <xref:System.Activities.Statements.Pick>Aktivita obsahuje kolekci <xref:System.Activities.Statements.PickBranch> objektů, z nichž jedna <xref:System.Activities.Statements.Pick> aktivita může být spuštěna z důvodu některé příchozí události, která slouží jako Trigger. Tímto způsobem [!INCLUDE[wfd1](../includes/wfd1-md.md)] poskytuje modelování toku řízení založené na událostech. Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A> . Na začátku <xref:System.Activities.Statements.Pick> provádění aktivity <xref:System.Activities.Statements.PickBranch> jsou naplánovány všechny aktivační aktivity prvků. Po dokončení první aktivity se naplánuje odpovídající aktivita akce a všechny ostatní aktivity triggeru se zruší.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak používat návrháře aktivity výběru
 Návrhář aktivity **výběru** se dá najít v kategorii **toku řízení** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panel nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář aktivity **výběru** lze přetáhnout ze **sady nástrojů** a na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěna návrháři aktivit, například uvnitř návrháře aktivity **sekvence** . Po přetažení se [!INCLUDE[wfd2](../includes/wfd2-md.md)] vytvoří <xref:System.Activities.Statements.Pick> aktivita, která ve výchozím nastavení obsahuje dvě prázdné <xref:System.Activities.Statements.PickBranch> aktivity jako prvky s zobrazovanými názvy pobočka1 a Branch2. Tyto odpovídající <xref:System.Activities.Statements.PickBranch.DisplayName%2A> hodnoty vlastností lze upravit v záhlaví návrháře aktivit **operace PickBranch** nebo v okně **vlastností** každé větve.

 Existují dva způsoby, jak přidat <xref:System.Activities.Statements.PickBranch> aktivity do kolekce <xref:System.Activities.Statements.Pick> objektu: přetahování návrháře **operace PickBranch** z **panelu nástrojů** nebo pomocí kontextové nabídky z návrhové plochy pro **Výběr** . Podrobnosti najdete v tématu [operace PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Všimněte si, že jediná položka, kterou lze umístit v Návrháři aktivity **výběru** , je Návrhář aktivity **operace PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Vybrat vlastnosti aktivity v Návrhář postupu provádění
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Pick> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje popisný název <xref:System.Activities.Statements.Pick> návrháře aktivit v hlavičce. Výchozí hodnota je vybrat. Hodnotu lze upravit v mřížce vlastností nebo přímo v záhlaví návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|

## <a name="see-also"></a>Viz také
 [Aktivita výběru](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [toku řízení](../workflow-designer/control-flow-activity-designers.md) [pomocí aktivity vybrat](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)