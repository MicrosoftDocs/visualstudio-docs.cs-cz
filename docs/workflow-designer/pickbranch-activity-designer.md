---
title: Návrhář aktivity Návrhář postupu provádění – operace PickBranch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a43fa99c9f5fe4fbb3cfe336efb983fced655f2a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650060"
---
# <a name="pickbranch-activity-designer"></a>Návrhář aktivity PickBranch

@No__t_0 poskytuje cestu založenou na událostech v rámci <xref:System.Activities.Statements.Pick> aktivity, kterou může aktivovat příchozí událost.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> objekty jsou obsaženy v kolekci <xref:System.Activities.Statements.Pick.Branches%2A> <xref:System.Activities.Statements.Pick> aktivity. Každá <xref:System.Activities.Statements.PickBranch> je obsažena ve větvi aktivity <xref:System.Activities.Statements.Pick> a lze ji provést z důvodu některé příchozí události, která slouží jako Trigger. Tímto způsobem Návrhář postupu provádění poskytuje modelování toku řízení založeného na událostech. Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak používat návrháře aktivity výběru

Přístup k Návrháři **operace PickBranch** v kategorii **toku řízení** v **sadě nástrojů**.

Dva prázdné <xref:System.Activities.Statements.PickBranch> objekty se zobrazovanými názvy **pobočka1** a **Branch2** jsou vytvořeny ve výchozím nastavení jako prvky aktivity <xref:System.Activities.Statements.Pick> při prvním vyřazení návrháře aktivit **výběru** do Návrhář postupu provádění. Tyto odpovídající hodnoty vlastností <xref:System.Activities.Statements.PickBranch.DisplayName%2A> lze upravit v záhlaví návrháře **operace PickBranch** nebo v okně **vlastností** každé větve.

Existují dva způsoby, jak přidat <xref:System.Activities.Statements.PickBranch> objektů do kolekce <xref:System.Activities.Statements.Pick> objektu: přetažení návrháře **operace PickBranch** ze **sady nástrojů**nebo pomocí místní nabídky na návrhové ploše pro **Výběr** :

- Návrhář **operace PickBranch** vytvoří <xref:System.Activities.Statements.PickBranch>, když je přetažena ze **sady nástrojů** a vyřazen do jedné z větví návrháře aktivity **výběru** na Návrhář postupu provádění povrchu. Nové objekty <xref:System.Activities.Statements.PickBranch> lze umístit do ovládacího prvku <xref:System.Activities.Statements.Pick> Designer vlevo nebo vpravo od všech existujících <xref:System.Activities.Statements.PickBranch> prvků, které jsou již obsaženy v kolekci. Při přetahování návrháře **operace PickBranch** do návrháře **výběru** pomocí myši, Návrhář **výběru** používá svislou modrou šedou plochu k označení, kde je <xref:System.Activities.Statements.PickBranch> přidáno pro dané umístění myši.

- Kliknutím pravým **tlačítkem myši na Návrhář aktivity Select** (ale ne uvnitř návrháře **operace PickBranch** ) Získejte kontextovou nabídku a výběrem možnosti **vytvořit větev** přidejte novou <xref:System.Activities.Statements.PickBranch>. Všimněte si, že nová <xref:System.Activities.Statements.PickBranch> je přidána napravo od existujících objektů <xref:System.Activities.Statements.PickBranch> v Návrháři **výběru** .

**Operace PickBranch** Designer se dá rozšířit tak, aby se zobrazila okna **triggeru** a **Akce** nebo sbalené kliknutím na dvojité blikající kurzory na pravé straně záhlaví. Upravte <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A> každého <xref:System.Activities.Statements.PickBranch> tím, že vyřadíte aktivity do polí **Trigger** a **Action** v jejich návrhářích.

Objekty <xref:System.Activities.Statements.PickBranch> v kolekci <xref:System.Activities.Statements.Pick.Branches%2A> objektu <xref:System.Activities.Statements.Pick> lze změnit jejich přetáhnutím na nové místo v Návrháři **výběru** . Návrhář **výběru** používá svislou modrou šedou pásma k označení, kde je <xref:System.Activities.Statements.PickBranch> přidáno pro dané umístění myši.

Existují dva způsoby, jak odstranit <xref:System.Activities.Statements.PickBranch>:

- Vyberte návrháře **operace PickBranch** a odstraňte ho.
- Vyberte návrháře **operace PickBranch** , klikněte pravým tlačítkem myši a získejte kontextovou nabídku a vyberte **Odstranit**.

Nezapomeňte vybrat návrháře **operace PickBranch** , protože výběrem jedné z aktivit uvnitř jeho **triggeru** nebo pole **akcí** omylem odstraníte jednu z těchto aktivit, nikoli objekt <xref:System.Activities.Statements.PickBranch>.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Operace PickBranch vlastnosti v Návrhář postupu provádění

Následující tabulka uvádí nejužitečnější vlastnosti <xref:System.Activities.Statements.PickBranch> a popisuje, jak je používat v Návrhář postupu provádění.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Popisný název zobrazený v záhlaví návrháře **operace PickBranch** Výchozí hodnota je větev.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Podmínka|Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> akci, která může vyvolat <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Action%2A>, který se spustí, když se aktivuje.|

## <a name="see-also"></a>Viz také:

- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
- [Výběr aktivity](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Použití aktivity Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)