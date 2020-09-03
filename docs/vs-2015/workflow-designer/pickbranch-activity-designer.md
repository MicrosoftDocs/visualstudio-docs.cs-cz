---
title: Návrhář aktivity operace PickBranch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c7c70aa8282fb8f50ed6faca5bcee3177ef81e15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672589"
---
# <a name="pickbranch-activity-designer"></a>Návrhář aktivity PickBranch
<xref:System.Activities.Statements.PickBranch>Poskytuje cestu založenou na událostech v rámci <xref:System.Activities.Statements.Pick> aktivity, kterou může aktivovat příchozí událost.

## <a name="pickbranch"></a>PickBranch
 <xref:System.Activities.Statements.PickBranch> objekty jsou obsaženy v <xref:System.Activities.Statements.Pick.Branches%2A> kolekci <xref:System.Activities.Statements.Pick> aktivity. Každá <xref:System.Activities.Statements.PickBranch> je obsažena ve větvi <xref:System.Activities.Statements.Pick> aktivity a lze ji provést z důvodu některé příchozí události, která slouží jako Trigger. Tímto způsobem [!INCLUDE[wfd1](../includes/wfd1-md.md)] poskytuje modelování toku řízení založené na událostech. Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A> .

### <a name="how-to-use-the-pick-activity-designer"></a>Jak používat návrháře aktivity výběru
 Návrhář **operace PickBranch** lze najít v kategorii **toku řízení** v **sadě nástrojů**, ke které se dostanete kliknutím na kartu **panel nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Dva prázdné <xref:System.Activities.Statements.PickBranch> objekty se zobrazovanými názvy **Pobočka1** a **Branch2** jsou vytvořeny ve výchozím nastavení jako prvky <xref:System.Activities.Statements.Pick> aktivity při počátečním zařazování návrháře aktivit **výběru** na [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Tyto odpovídající <xref:System.Activities.Statements.PickBranch.DisplayName%2A> hodnoty vlastností lze upravit v záhlaví návrháře **operace PickBranch** nebo v okně **vlastností** každé větve.

 Existují dva způsoby, jak přidat <xref:System.Activities.Statements.PickBranch> objekty do kolekce <xref:System.Activities.Statements.Pick> objektu: přetažení návrháře **operace PickBranch** z **panelu nástrojů** nebo pomocí kontextové nabídky z návrhové plochy pro **Výběr** :

1. Návrhář **operace PickBranch** vytvoří, <xref:System.Activities.Statements.PickBranch> když je přetažen ze **sady nástrojů** a vyřazen do jedné z větví návrháře aktivity **výběru** na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu. Nové <xref:System.Activities.Statements.PickBranch> objekty lze umístit do <xref:System.Activities.Statements.Pick> Návrháře vlevo nebo vpravo od všech existujících prvků, které <xref:System.Activities.Statements.PickBranch> jsou již obsaženy v kolekci. Když přetáhnete návrháře **operace PickBranch** do návrháře **výběru** pomocí myši, Návrhář **výběru** použije svislou modrou šedou plochu k označení, kde <xref:System.Activities.Statements.PickBranch> je přidáno pro dané umístění myši.

2. Pokud chcete získat kontextovou nabídku, klikněte pravým tlačítkem myši na možnost **Vybrat** Návrhář aktivity (ale ne uvnitř návrháře **operace PickBranch** ) a vyberte **vytvořit větev** pro přidání nového <xref:System.Activities.Statements.PickBranch> . Všimněte si, že nová <xref:System.Activities.Statements.PickBranch> je přidána napravo od existujících <xref:System.Activities.Statements.PickBranch> objektů v Návrháři **výběru** .

   **Operace PickBranch** Designer se dá rozšířit tak, aby se zobrazila okna **triggeru** a **Akce** nebo sbalené kliknutím na dvojité blikající kurzory na pravé straně záhlaví. Upravte <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A> pro každou z nich <xref:System.Activities.Statements.PickBranch> vyřazením aktivit do polí **Trigger** a **Action** v jejich návrhářích.

   <xref:System.Activities.Statements.PickBranch>Objekty v <xref:System.Activities.Statements.Pick.Branches%2A> kolekci <xref:System.Activities.Statements.Pick> objektu lze přeuspořádat přetažením a přetažením do nového umístění v rámci návrháře **výběru** . Návrhář **výběru** používá svislou modrou a šedý pruh k označení, kde <xref:System.Activities.Statements.PickBranch> je přidáno pro dané umístění myši.

   Existují dva způsoby, jak odstranit <xref:System.Activities.Statements.PickBranch> :

3. Vyberte návrháře **operace PickBranch** a odstraňte ho.

4. Vyberte návrháře **operace PickBranch** , klikněte pravým tlačítkem myši a získejte kontextovou nabídku a vyberte **Odstranit**.

   Nezapomeňte vybrat **operace PickBranch** Designer, protože výběrem jedné z aktivit uvnitř jeho **triggeru** nebo pole **akcí** omylem odstraníte jednu z těchto aktivit, nikoli <xref:System.Activities.Statements.PickBranch> objekt.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Operace PickBranch vlastnosti v Návrhář postupu provádění
 Následující tabulka uvádí nejužitečnější <xref:System.Activities.Statements.PickBranch> vlastnosti a popisuje jejich použití v nástroji [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Ne|Popisný název zobrazený v záhlaví návrháře **operace PickBranch** Výchozí hodnota je větev.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Ano|Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> akci, která může vyvolat <xref:System.Activities.Statements.PickBranch.Action%2A> .|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Ne|Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Action%2A> , který se spustí, když se aktivuje.|

## <a name="see-also"></a>Viz také
 [Aktivita výběru](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [toku řízení](../workflow-designer/control-flow-activity-designers.md) [pomocí aktivity vybrat](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)