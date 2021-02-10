---
title: Návrhář aktivit pro výběr Návrhář postupu provádění
description: Přečtěte si, jak aktivita výběru poskytuje tok řízení založený na událostech a v reakci na triggerovou událost spouští jednu z několika větví.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b616cf3d9b7eba5b2a2e9de23546a8a5f9c36ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968694"
---
# <a name="pick-activity-designer"></a>Návrhář aktivity Pick

<xref:System.Activities.Statements.Pick>Aktivita poskytuje tok řízení založený na událostech. Aktivita spustí jednu z několika větví v reakci na událost triggeru.

## <a name="the-pick-activity"></a>Aktivita výběru

<xref:System.Activities.Statements.Pick>Aktivita obsahuje kolekci <xref:System.Activities.Statements.PickBranch> objektů, z nichž jedna <xref:System.Activities.Statements.Pick> aktivita může být spuštěna z důvodu některé příchozí události, která slouží jako Trigger. Tímto způsobem Návrhář postupu provádění poskytuje modelování toku řízení založené na událostech. Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A> . Na začátku <xref:System.Activities.Statements.Pick> provádění aktivity <xref:System.Activities.Statements.PickBranch> jsou naplánovány všechny aktivační aktivity prvků. Po dokončení první aktivity se naplánuje odpovídající aktivita akce a všechny ostatní aktivity triggeru se zruší.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak používat návrháře aktivity výběru

Přístup k Návrháři aktivity **výběru** v kategorii **tok řízení** v **sadě nástrojů**. Návrhář aktivity **výběru** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěna návrháři aktivit, například uvnitř návrháře aktivity **sekvence** . Po přetažení do Návrhář postupu provádění vytvoří <xref:System.Activities.Statements.Pick> aktivitu, která ve výchozím nastavení obsahuje dvě prázdné <xref:System.Activities.Statements.PickBranch> aktivity jako prvky se zobrazovanými názvy Pobočka1 a Branch2. Tyto odpovídající <xref:System.Activities.Statements.PickBranch.DisplayName%2A> hodnoty vlastností lze upravit v záhlaví návrháře aktivit **operace PickBranch** nebo v okně **vlastností** každé větve.

Existují dva způsoby, jak přidat <xref:System.Activities.Statements.PickBranch> aktivity do kolekce <xref:System.Activities.Statements.Pick> objektu: přetahování návrháře **operace PickBranch** z **panelu nástrojů** nebo pomocí místní nabídky na návrhové ploše pro **Výběr** . Podrobnosti najdete v tématu [operace PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Všimněte si, že jediná položka, kterou lze umístit v Návrháři aktivity **výběru** , je Návrhář aktivity **operace PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Vybrat vlastnosti aktivity v Návrhář postupu provádění

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Pick> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje popisný název <xref:System.Activities.Statements.Pick> návrháře aktivit v hlavičce. Výchozí hodnota je vybrat. Hodnotu lze upravit v mřížce vlastností nebo přímo v záhlaví návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|

## <a name="see-also"></a>Viz také

- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
- [Výběr aktivity](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Použití aktivity Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)