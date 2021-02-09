---
title: Návrhář aktivity Návrhář postupu provádění – paralelní
description: Přečtěte si o paralelní aktivitě a o tom, jak používat návrháře paralelních aktivit k souběžnému spuštění kolekce podřízených aktivit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3997b72105c22f10500559370d8a23faaa2f24eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905164"
---
# <a name="parallel-activity-designer"></a>Návrhář aktivity Parallel

Tato <xref:System.Activities.Statements.Parallel> aktivita provádí souběžnou kolekci podřízených aktivit.

## <a name="the-parallel-activity"></a>Paralelní aktivita

<xref:System.Activities.Statements.Parallel>Aktivita ukládá své podřízené aktivity do <xref:System.Activities.Statements.Parallel.Branches%2A> kolekce. Tuto <xref:System.Activities.Statements.Parallel> aktivitu použijte místo aktivity, <xref:System.Activities.Statements.Sequence> Pokud některé z podřízených aktivit můžou přijít na nečinné.

<xref:System.Activities.Statements.Parallel>Aktivita má <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> vlastnost, která obsahuje uživatelem zadanou Visual Basic výraz. <xref:System.Activities.Statements.Parallel>Aktivita vyhodnotí tuto vlastnost po dokončení každé větve. Pokud se vyhodnotí jako **true**, <xref:System.Activities.Statements.Parallel> aktivita se dokončí bez provedení ostatních větví. Pokud se <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nevyhodnotí jako **true**, aktivita se <xref:System.Activities.Statements.Parallel> dokončí po dokončení všech jejích podřízených aktivit.

### <a name="using-the-parallel-activity-designer"></a>Použití návrháře paralelní aktivity

Přístup k Návrháři **paralelní** aktivity v kategorii **tok řízení** v **sadě nástrojů**.

Návrhář **paralelní** aktivity lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěna návrháři aktivit, například uvnitř návrháře aktivity **sekvence** . Po přetažení do Návrhář postupu provádění vytvoří <xref:System.Activities.Statements.Parallel> aktivitu, která ve výchozím nastavení obsahuje <xref:System.Activities.Activity.DisplayName%2A> **paralelní**

Chcete-li přidat aktivitu do <xref:System.Activities.Statements.Parallel.Branches%2A> kolekce paralelní aktivity, přetáhněte z **panelu nástrojů** jiný Návrhář aktivity a umístěte jej na trojúhelník v Návrháři **paralelní** aktivity. Trojúhelníky procházely činnostmi obsaženými v větvích. Další aktivity lze přidat opakováním tohoto postupu. Pořadí aktivit lze změnit přetažením v Návrháři **paralelní** aktivity.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Vlastnosti paralelní aktivity v Návrhář postupu provádění

V následující tabulce jsou uvedeny vlastnosti paralelní aktivity a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje popisný zobrazovaný název návrháře aktivit v hlavičce. Výchozí hodnota je **Parallel**. Hodnota může být volitelně upravena v mřížce **vlastnosti** nebo přímo v hlavičce návrháře aktivit.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Ano|Obsahuje kolekci podřízených aktivit, které mají být provedeny.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Ne|Vyhodnoceno po dokončení větve. Pokud se vyhodnotí jako **true**, naplánovaných nevyřízených větví se zruší. Pokud tato vlastnost není nastavená nebo se vyhodnotí jako **false**, aktivita se dokončí po dokončení všech jejích podřízených aktivit. Výchozí hodnota je **null**.|

## <a name="see-also"></a>Viz také

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
