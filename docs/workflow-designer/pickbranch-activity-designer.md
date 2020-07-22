---
title: Návrhář aktivity Návrhář postupu provádění – operace PickBranch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34da9091c0f96b7270678f9b36fe861e4a87418f
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876083"
---
# <a name="pickbranch-activity-designer"></a>Návrhář aktivity PickBranch

<xref:System.Activities.Statements.PickBranch>Poskytuje cestu založenou na událostech v rámci <xref:System.Activities.Statements.Pick> aktivity, kterou může aktivovat příchozí událost.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch>objekty jsou obsaženy v <xref:System.Activities.Statements.Pick.Branches%2A> kolekci <xref:System.Activities.Statements.Pick> aktivity. Každá <xref:System.Activities.Statements.PickBranch> je obsažena ve větvi <xref:System.Activities.Statements.Pick> aktivity a lze ji provést z důvodu některé příchozí události, která slouží jako Trigger. Tímto způsobem Návrhář postupu provádění poskytuje modelování toku řízení založeného na událostech. Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A> .

### <a name="how-to-use-the-pick-activity-designer"></a>Jak používat návrháře aktivity výběru

Přístup k Návrháři **operace PickBranch** v kategorii **toku řízení** v **sadě nástrojů**.

Dva prázdné <xref:System.Activities.Statements.PickBranch> objekty se zobrazovanými názvy **Pobočka1** a **Branch2** jsou vytvořeny ve výchozím nastavení jako prvky <xref:System.Activities.Statements.Pick> aktivity při počátečním zařazování návrháře aktivit **výběru** na Návrhář postupu provádění. Tyto odpovídající <xref:System.Activities.Statements.PickBranch.DisplayName%2A> hodnoty vlastností lze upravit v záhlaví návrháře **operace PickBranch** nebo v okně **vlastností** každé větve.

Existují dva způsoby, jak přidat <xref:System.Activities.Statements.PickBranch> objekty do kolekce <xref:System.Activities.Statements.Pick> objektu: přetažení návrháře **operace PickBranch** ze **sady nástrojů**nebo pomocí místní nabídky na návrhové ploše pro **Výběr** :

- Návrhář **operace PickBranch** vytvoří, <xref:System.Activities.Statements.PickBranch> když je přetažen ze **sady nástrojů** a vyřazen do jedné z větví návrháře aktivity **výběru** na Návrhář postupu provádění povrchu. Nové <xref:System.Activities.Statements.PickBranch> objekty lze umístit do <xref:System.Activities.Statements.Pick> Návrháře vlevo nebo vpravo od všech existujících prvků, které <xref:System.Activities.Statements.PickBranch> jsou již obsaženy v kolekci. Když přetáhnete návrháře **operace PickBranch** do návrháře **výběru** pomocí myši, Návrhář **výběru** použije svislou modrou šedou plochu k označení, kde <xref:System.Activities.Statements.PickBranch> je přidáno pro dané umístění myši.

- Kliknutím pravým **tlačítkem myši na Návrhář aktivity Select** (ale ne uvnitř návrháře **operace PickBranch** ) Získejte kontextovou nabídku a výběrem možnosti **vytvořit větev** přidejte novou <xref:System.Activities.Statements.PickBranch> . Všimněte si, že nová <xref:System.Activities.Statements.PickBranch> je přidána napravo od existujících <xref:System.Activities.Statements.PickBranch> objektů v Návrháři **výběru** .

**Operace PickBranch** Designer se dá rozšířit tak, aby se zobrazila okna **triggeru** a **Akce** nebo sbalené kliknutím na dvojité blikající kurzory na pravé straně záhlaví. Upravte <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A> pro každou z nich <xref:System.Activities.Statements.PickBranch> vyřazením aktivit do polí **Trigger** a **Action** v jejich návrhářích.

<xref:System.Activities.Statements.PickBranch>Objekty v <xref:System.Activities.Statements.Pick.Branches%2A> kolekci <xref:System.Activities.Statements.Pick> objektu lze přeuspořádat přetažením a přetažením do nového umístění v rámci návrháře **výběru** . Návrhář **výběru** používá svislou modrou a šedý pruh k označení, kde <xref:System.Activities.Statements.PickBranch> je přidáno pro dané umístění myši.

Existují dva způsoby, jak odstranit <xref:System.Activities.Statements.PickBranch> :

- Vyberte návrháře **operace PickBranch** a odstraňte ho.
- Vyberte návrháře **operace PickBranch** , klikněte pravým tlačítkem myši a získejte kontextovou nabídku a vyberte **Odstranit**.

Nezapomeňte vybrat **operace PickBranch** Designer, protože výběrem jedné z aktivit uvnitř jeho **triggeru** nebo pole **akcí** omylem odstraníte jednu z těchto aktivit, nikoli <xref:System.Activities.Statements.PickBranch> objekt.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Operace PickBranch vlastnosti v Návrhář postupu provádění

Následující tabulka uvádí nejužitečnější <xref:System.Activities.Statements.PickBranch> vlastnosti a popisuje jejich použití v Návrhář postupu provádění.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Nepravda|Popisný název zobrazený v záhlaví návrháře **operace PickBranch** Výchozí hodnota je větev.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Ano|Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> akci, která může vyvolat <xref:System.Activities.Statements.PickBranch.Action%2A> .|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Nepravda|Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Action%2A> , který se spustí, když se aktivuje.|

## <a name="see-also"></a>Viz také

- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
- [Výběr aktivity](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Použití aktivity Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)