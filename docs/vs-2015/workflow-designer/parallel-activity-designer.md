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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672640"
---
# <a name="parallel-activity-designer"></a>Návrhář aktivity Parallel
Tato <xref:System.Activities.Statements.Parallel> aktivita provádí souběžnou kolekci podřízených aktivit.

## <a name="the-parallel-activity"></a>Paralelní aktivita
 <xref:System.Activities.Statements.Parallel>Aktivita ukládá své podřízené aktivity do <xref:System.Activities.Statements.Parallel.Branches%2A> kolekce. Tuto <xref:System.Activities.Statements.Parallel> aktivitu použijte místo aktivity, <xref:System.Activities.Statements.Sequence> Pokud některé z podřízených aktivit můžou přijít na nečinné.

 <xref:System.Activities.Statements.Parallel>Aktivita má <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> vlastnost, která obsahuje výraz zadaný uživatelem [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . <xref:System.Activities.Statements.Parallel>Aktivita vyhodnotí tuto vlastnost po dokončení každé větve. Pokud se vyhodnotí jako **true**, <xref:System.Activities.Statements.Parallel> aktivita se dokončí bez provedení ostatních větví. Pokud se <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nevyhodnotí jako **true**, aktivita se <xref:System.Activities.Statements.Parallel> dokončí po dokončení všech jejích podřízených aktivit.

### <a name="using-the-parallel-activity-designer"></a>Použití návrháře paralelní aktivity
 Návrhář **paralelní** aktivity lze najít v kategorii **tok řízení** na **panelu nástrojů**, ke kterému se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Návrhář **paralelní** aktivity lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, ať jsou obvykle umístěna návrháři aktivit, například uvnitř návrháře aktivity **sekvence** . Po přetažení do rozhraní [!INCLUDE[wfd2](../includes/wfd2-md.md)] vytvoří <xref:System.Activities.Statements.Parallel> aktivitu, která ve výchozím nastavení obsahuje <xref:System.Activities.Activity.DisplayName%2A> **paralelní**

 Chcete-li přidat aktivitu do <xref:System.Activities.Statements.Parallel.Branches%2A> kolekce paralelní aktivity, přetáhněte z **panelu nástrojů** jiný Návrhář aktivity a umístěte jej na trojúhelník v Návrháři **paralelní** aktivity. Trojúhelníky procházely činnostmi obsaženými v větvích. Další aktivity lze přidat opakováním tohoto postupu. Pořadí aktivit lze změnit přetažením v Návrháři **paralelní** aktivity.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Vlastnosti paralelní aktivity v Návrhář postupu provádění
 V následující tabulce jsou uvedeny vlastnosti paralelní aktivity a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje popisný zobrazovaný název návrháře aktivit v hlavičce. Výchozí hodnota je **Parallel**. Hodnota může být volitelně upravena v mřížce **vlastnosti** nebo přímo v hlavičce návrháře aktivit.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Ano|Obsahuje kolekci podřízených aktivit, které mají být provedeny.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Ne|Vyhodnoceno po dokončení větve. Pokud se vyhodnotí jako **true**, naplánovaných nevyřízených větví se zruší. Pokud tato vlastnost není nastavená nebo se vyhodnotí jako **false**, aktivita se dokončí po dokončení všech jejích podřízených aktivit. Výchozí hodnota je **null**.|

## <a name="see-also"></a>Viz také
 [Sekvenční](../workflow-designer/sequence-activity-designer.md) [tok řízení](../workflow-designer/control-flow-activity-designers.md) [ \<T> ParallelForEach](../workflow-designer/parallelforeach-t-activity-designer.md)