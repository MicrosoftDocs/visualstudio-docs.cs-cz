---
title: Návrhář aktivit pro výběr Návrhář postupu provádění
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 983a3ee3539617bf7ee5864c2138b2f0369e228f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650081"
---
# <a name="pick-activity-designer"></a>Návrhář aktivity Pick

Aktivita <xref:System.Activities.Statements.Pick> poskytuje tok řízení založený na událostech. Aktivita spustí jednu z několika větví v reakci na událost triggeru.

## <a name="the-pick-activity"></a>Aktivita výběru

Aktivita <xref:System.Activities.Statements.Pick> obsahuje kolekci objektů <xref:System.Activities.Statements.PickBranch>, z nichž jedna <xref:System.Activities.Statements.Pick> aktivita může být spuštěna z důvodu některé příchozí události, která slouží jako Trigger. Tímto způsobem Návrhář postupu provádění poskytuje modelování toku řízení založené na událostech. Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A>. Na začátku provádění <xref:System.Activities.Statements.Pick> aktivity se naplánují všechny aktivační aktivity prvků <xref:System.Activities.Statements.PickBranch>. Po dokončení první aktivity se naplánuje odpovídající aktivita akce a všechny ostatní aktivity triggeru se zruší.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak používat návrháře aktivity výběru

Přístup k Návrháři aktivity **výběru** v kategorii **tok řízení** v **sadě nástrojů**. Návrhář aktivity **výběru** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěna návrháři aktivit, například uvnitř návrháře aktivity **sekvence** . Po přetažení do Návrhář postupu provádění vytvoří aktivitu <xref:System.Activities.Statements.Pick>, která ve výchozím nastavení obsahuje dvě prázdné <xref:System.Activities.Statements.PickBranch> aktivity jako prvky s zobrazovanými názvy Pobočka1 a Branch2. Tyto odpovídající hodnoty vlastností <xref:System.Activities.Statements.PickBranch.DisplayName%2A> lze upravit v záhlaví návrháře aktivit **operace PickBranch** nebo v okně **vlastnosti** pro každou větev.

Existují dva způsoby, jak přidat <xref:System.Activities.Statements.PickBranch> aktivity do kolekce <xref:System.Activities.Statements.Pick> objektu: přetahování návrháře **operace PickBranch** z **panelu nástrojů** nebo pomocí místní nabídky v rámci návrhové plochy pro **Výběr** . Podrobnosti najdete v tématu [operace PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Všimněte si, že jediná položka, kterou lze umístit v Návrháři aktivity **výběru** , je Návrhář aktivity **operace PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Vybrat vlastnosti aktivity v Návrhář postupu provádění

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.Pick> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje popisný název návrháře <xref:System.Activities.Statements.Pick> aktivity v hlavičce. Výchozí hodnota je vybrat. Hodnotu lze upravit v mřížce vlastností nebo přímo v záhlaví návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|

## <a name="see-also"></a>Viz také:

- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
- [Výběr aktivity](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Použití aktivity Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)