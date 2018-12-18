---
title: Návrhář aktivity Pick | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f0a3d5487d60a796f8bf9727c07df1afc959de5c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221517"
---
# <a name="pick-activity-designer"></a>Návrhář aktivity Pick
<xref:System.Activities.Statements.Pick> Poskytuje aktivity toku řízení založené na událostech. Tato aktivity spustí jednu z několika větví v reakci na aktivační událost.  
  
## <a name="the-pick-activity"></a>Aktivity Pick  
 A <xref:System.Activities.Statements.Pick> aktivita obsahuje kolekci <xref:System.Activities.Statements.PickBranch> objektů, z nichž jeden <xref:System.Activities.Statements.Pick> aktivity můžete spustit z důvodu některých příchozí události, která slouží jako trigger. Tímto způsobem [!INCLUDE[wfd1](../includes/wfd1-md.md)] poskytuje modelování toku řízení na základě událostí. Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A>. Na začátku <xref:System.Activities.Statements.Pick> provádění aktivity, všechny aktivační události aktivity <xref:System.Activities.Statements.PickBranch> prvky jsou naplánovány. Po dokončení první aktivitu naplánované odpovídající akci aktivity a všech ostatních aktivit. aktivační událost se zruší.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Jak používat návrháře aktivit výběr  
 **Vyberte** návrháře aktivit najdete v **tok řízení** kategorii **nástrojů**, který přistupuje po kliknutí **nástrojů**kartě [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte možnost **nástrojů** z **zobrazení** nabídky nebo CTRL + ALT + X.)  
  
 **Vyberte** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřazené k [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface všude, kde návrháři aktivit jsou obvykle umístěny, například uvnitř  **Pořadí** návrháře aktivit. Po vyřazení do [!INCLUDE[wfd2](../includes/wfd2-md.md)], vytváří <xref:System.Activities.Statements.Pick> aktivitu, která ve výchozím nastavení obsahuje dva prázdné <xref:System.Activities.Statements.PickBranch> aktivitám v podobě elementů pomocí zobrazení názvů pobočka1 a Branch2. Tyto příslušných <xref:System.Activities.Statements.PickBranch.DisplayName%2A> hodnoty vlastností lze upravovat ve službě **PickBranch** návrháře záhlaví činnosti nebo v rámci **vlastnosti** okna pro každou větev.  
  
 Existují dva způsoby, jak přidat <xref:System.Activities.Statements.PickBranch> aktivity do kolekce <xref:System.Activities.Statements.Pick> objektu: přetahování a vkládání **PickBranch** z návrháře **nástrojů** nebo pomocí místní nabídky z v rámci **vyberte** návrhovou plochu. Podrobnosti najdete v tématu [PickBranch](../workflow-designer/pickbranch-activity-designer.md) tématu. Všimněte si, že pouze položky, které je možné použít uvnitř **vyberte** je Návrhář aktivity **PickBranch** návrháře aktivit.  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>Vybrat vlastnosti aktivit v Návrháři postupu provádění  
 Následující tabulka ukazuje <xref:System.Activities.Statements.Pick> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností nebo na návrhové ploše.  
  
|Název vlastnosti|Požadováno|Použití|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje popisný název <xref:System.Activities.Statements.Pick> návrháře aktivit v záhlaví. Výchozí hodnota je výběr. Hodnotu lze upravit v mřížce vlastností nebo přímo v hlavičce návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je osvědčeným postupem je použití jednoho.|  
  
## <a name="see-also"></a>Viz také  
 [Tok řízení](../workflow-designer/control-flow-activity-designers.md)   
 [Výběr aktivity](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Použití aktivity Pick](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)