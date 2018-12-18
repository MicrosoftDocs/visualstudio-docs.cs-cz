---
title: Návrhář postupu provádění – Návrhář aktivity Pick
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5bd37c78567ea11d53899bcbaefb2e3809a00057
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826008"
---
# <a name="pick-activity-designer"></a>Návrhář aktivity Pick

<xref:System.Activities.Statements.Pick> Poskytuje aktivity toku řízení založené na událostech. Tato aktivity spustí jednu z několika větví v reakci na aktivační událost.

## <a name="the-pick-activity"></a>Aktivity Pick

A <xref:System.Activities.Statements.Pick> aktivita obsahuje kolekci <xref:System.Activities.Statements.PickBranch> objektů, z nichž jeden <xref:System.Activities.Statements.Pick> aktivity můžete spustit z důvodu některých příchozí události, která slouží jako trigger. Tímto způsobem Návrhář postupu provádění umožňuje modelování toku řízení na základě událostí. Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A>. Na začátku <xref:System.Activities.Statements.Pick> provádění aktivity, všechny aktivační události aktivity <xref:System.Activities.Statements.PickBranch> prvky jsou naplánovány. Po dokončení první aktivitu naplánované odpovídající akci aktivity a všech ostatních aktivit. aktivační událost se zruší.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak používat návrháře aktivit výběr

Přístup **vyberte** návrháře aktivit v **tok řízení** kategorii **nástrojů**. **Vyberte** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění bez ohledu na to návrháři aktivit jsou obvykle umístěny, například uvnitř  **Pořadí** návrháře aktivit. Po jeho umístěním do návrháře postupu provádění, vytvoří <xref:System.Activities.Statements.Pick> aktivitu, která ve výchozím nastavení obsahuje dva prázdné <xref:System.Activities.Statements.PickBranch> aktivitám v podobě elementů pomocí zobrazení názvů pobočka1 a Branch2. Tyto příslušných <xref:System.Activities.Statements.PickBranch.DisplayName%2A> hodnoty vlastností lze upravovat ve službě **PickBranch** návrháře záhlaví činnosti nebo v rámci **vlastnosti** okna pro každou větev.

Existují dva způsoby, jak přidat <xref:System.Activities.Statements.PickBranch> aktivity do kolekce <xref:System.Activities.Statements.Pick> objektu: přetahování a vkládání **PickBranch** z návrháře **nástrojů** nebo pomocí místní nabídky z v rámci **vyberte** návrhovou plochu. Podrobnosti najdete v tématu [PickBranch](../workflow-designer/pickbranch-activity-designer.md) tématu. Všimněte si, že pouze položky, které je možné použít uvnitř **vyberte** je Návrhář aktivity **PickBranch** návrháře aktivit.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Vybrat vlastnosti aktivit v Návrháři postupu provádění

Následující tabulka ukazuje <xref:System.Activities.Statements.Pick> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje popisný název <xref:System.Activities.Statements.Pick> návrháře aktivit v záhlaví. Výchozí hodnota je výběr. Hodnotu lze upravit v mřížce vlastností nebo přímo v hlavičce návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je osvědčeným postupem je použití jednoho.|

## <a name="see-also"></a>Viz také:

- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
- [Výběr aktivity](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Použití aktivity Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)