---
title: Návrhář paralelních aktivit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a46a340ccdeacacb8f04b962313db18975447a67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672640"
---
# <a name="parallel-activity-designer"></a>Návrhář aktivity Parallel
Aktivita <xref:System.Activities.Statements.Parallel> spouští souběžnou kolekci podřízených aktivit.

## <a name="the-parallel-activity"></a>Paralelní aktivita
 Aktivita <xref:System.Activities.Statements.Parallel> ukládá své podřízené aktivity do kolekce <xref:System.Activities.Statements.Parallel.Branches%2A>. Pokud některé z podřízených aktivit můžou přijít na nečinné, použijte aktivitu <xref:System.Activities.Statements.Parallel> místo <xref:System.Activities.Statements.Sequence> aktivity.

 Aktivita <xref:System.Activities.Statements.Parallel> má vlastnost <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>, která obsahuje [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]ho výrazu zadaného uživatelem. Aktivita <xref:System.Activities.Statements.Parallel> vyhodnotí tuto vlastnost po dokončení každé větve. Pokud se vyhodnotí jako **true**, <xref:System.Activities.Statements.Parallel> aktivita se dokončí bez provedení ostatních větví. Pokud se <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nevyhodnotí jako **true**, pak se <xref:System.Activities.Statements.Parallel> aktivita dokončí po dokončení všech jejích podřízených aktivit.

### <a name="using-the-parallel-activity-designer"></a>Použití návrháře paralelní aktivity
 Návrhář **paralelní** aktivity lze najít v kategorii **tok řízení** na **panelu nástrojů**, ke kterému se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte **panel nástrojů** zV nabídce Zobrazit nebo CTRL + ALT + X.)

 Návrhář **paralelní** aktivity lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěna návrháři aktivit, například uvnitř návrháře aktivity **sekvence** . Po přetažení do [!INCLUDE[wfd2](../includes/wfd2-md.md)] vytvoří aktivitu <xref:System.Activities.Statements.Parallel>, která ve výchozím nastavení obsahuje <xref:System.Activities.Activity.DisplayName%2A> **Parallel** .

 Chcete-li přidat aktivitu do kolekce <xref:System.Activities.Statements.Parallel.Branches%2A> paralelní aktivity, přetáhněte z **panelu nástrojů** jiný Návrhář aktivity a umístěte jej na trojúhelník uvnitř návrháře **paralelních** aktivit. Trojúhelníky procházely činnostmi obsaženými v větvích. Další aktivity lze přidat opakováním tohoto postupu. Pořadí aktivit lze změnit přetažením v Návrháři **paralelní** aktivity.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Vlastnosti paralelní aktivity v Návrhář postupu provádění
 V následující tabulce jsou uvedeny vlastnosti paralelní aktivity a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje popisný zobrazovaný název návrháře aktivit v hlavičce. Výchozí hodnota je **Parallel**. Hodnota může být volitelně upravena v mřížce **vlastnosti** nebo přímo v hlavičce návrháře aktivit.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Podmínka|Obsahuje kolekci podřízených aktivit, které mají být provedeny.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Vyhodnoceno po dokončení větve. Pokud se vyhodnotí jako **true**, naplánovaných nevyřízených větví se zruší. Pokud tato vlastnost není nastavená nebo se vyhodnotí jako **false**, aktivita se dokončí po dokončení všech jejích podřízených aktivit. Výchozí hodnota je **null**.|

## <a name="see-also"></a>Viz také
 [Tok řízení](../workflow-designer/control-flow-activity-designers.md) [ParallelForEach \<T](../workflow-designer/parallelforeach-t-activity-designer.md) [sekvence](../workflow-designer/sequence-activity-designer.md) >