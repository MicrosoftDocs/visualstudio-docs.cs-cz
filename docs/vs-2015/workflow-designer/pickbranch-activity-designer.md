---
title: Návrhář aktivity PickBranch | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f39479c9421ab87caf7c918e05be89272f0fb4de
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887302"
---
# <a name="pickbranch-activity-designer"></a>Návrhář aktivity PickBranch
<xref:System.Activities.Statements.PickBranch> Poskytuje cesta provádění v rámci založené na událostech <xref:System.Activities.Statements.Pick> aktivitu, která mohou být spouštěny příchozí události.  
  
## <a name="pickbranch"></a>Operace PickBranch  
 <xref:System.Activities.Statements.PickBranch> objekty jsou součástí <xref:System.Activities.Statements.Pick.Branches%2A> kolekce <xref:System.Activities.Statements.Pick> aktivity. Každý <xref:System.Activities.Statements.PickBranch> nachází ve větvi <xref:System.Activities.Statements.Pick> aktivity a je možné provést kvůli některé příchozí události, která slouží jako trigger. V tomto stejně, jako je [!INCLUDE[wfd1](../includes/wfd1-md.md)] poskytuje modelování toku řízení na základě událostí. Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Jak používat návrháře aktivit výběr  
 **PickBranch** návrháře najdete v **tok řízení** kategorii **nástrojů**, který přistupuje po kliknutí **nástrojů** na kartě [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte možnost **nástrojů** z **zobrazení** nabídky nebo CTRL + ALT + X).  
  
 Dva prázdné <xref:System.Activities.Statements.PickBranch> objekty se zobrazí názvy **pobočka1** a **Branch2** byly vytvořeny ve výchozím nastavení jako prvky <xref:System.Activities.Statements.Pick> aktivity při **vyberte** Návrhář aktivity je zpočátku vyřadit k [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Tyto příslušných <xref:System.Activities.Statements.PickBranch.DisplayName%2A> hodnoty vlastností lze upravovat ve službě **PickBranch** návrháře záhlaví nebo v rámci **vlastnosti** okna pro každou větev.  
  
 Existují dva způsoby, jak přidat <xref:System.Activities.Statements.PickBranch> objektů do kolekce <xref:System.Activities.Statements.Pick> objektu: přetahování a vkládání **PickBranch** z návrháře **nástrojů** nebo pomocí místní nabídky z v rámci **vyberte** návrhové plochy:  
  
1. **PickBranch** Návrhář vytvoří <xref:System.Activities.Statements.PickBranch> při je přetažen z **nástrojů** a vyřadit do jednoho z pobočky **vyberte** Návrhář aktivity na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu. Nové <xref:System.Activities.Statements.PickBranch> objekty mohou být umístěny uvnitř <xref:System.Activities.Statements.Pick> návrháře nalevo nebo napravo od všechny existující <xref:System.Activities.Statements.PickBranch> prvky, které jsou již v kolekci obsažena. Při přetažení **PickBranch** návrháře na **vyberte** návrháře myší, **vyberte** Návrhář používá svislé šedé modrá obsluhy vzdálené správy na uveďte, kam <xref:System.Activities.Statements.PickBranch> Přidá se pro daný myši umístění.  
  
2. Klikněte pravým tlačítkem myši **vyberte** Návrhář aktivity (, ale ne uvnitř **PickBranch** návrháře) získat kontextovou nabídku a vyberte **vytvořit větev** přidáte nový <xref:System.Activities.Statements.PickBranch>. Všimněte si, že nový <xref:System.Activities.Statements.PickBranch> přidá napravo od existující <xref:System.Activities.Statements.PickBranch> objekty v **vyberte** návrháře.  
  
   **PickBranch** návrháře se rozšířit zobrazíte **aktivační událost** a **akce** pole nebo sbalena klepnutím double střížek na pravé straně jejich záhlaví. Upravit <xref:System.Activities.Statements.PickBranch.Trigger%2A> a <xref:System.Activities.Statements.PickBranch.Action%2A> jednotlivých <xref:System.Activities.Statements.PickBranch> přetažením aktivity do **aktivační událost** a **akce** polí jejich návrhářů.  
  
   <xref:System.Activities.Statements.PickBranch> Objekty v <xref:System.Activities.Statements.Pick.Branches%2A> kolekce <xref:System.Activities.Statements.Pick> objektu, může být přeuspořádány přetahováním do nového umístění v rámci **vyberte** návrháře. **Vyberte** Návrhář používá svislé šedé modrá obsluhy vzdálené správy na uveďte, kam <xref:System.Activities.Statements.PickBranch> se přidá k umístění dané myši.  
  
   Existují dva způsoby, jak odstranit <xref:System.Activities.Statements.PickBranch>:  
  
3. Vyberte **PickBranch** návrháře a odstraňte ho.  
  
4. Vyberte **PickBranch** návrháře, klikněte pravým tlačítkem a v místní nabídce získala a vybrala **odstranit**.  
  
   Je nutné vybrat **PickBranch** návrháře, jako když vyberete některý z aktivit uvnitř jeho **aktivační událost** nebo **akce** polí omylem odstraní, jednu z těchto aktivit a ne <xref:System.Activities.Statements.PickBranch> objektu.  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>Operace PickBranch vlastnosti v Návrháři postupu provádění  
 V následující tabulce jsou uvedeny nejužitečnější <xref:System.Activities.Statements.PickBranch> vlastnosti a popisuje, jak používat [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Název vlastnosti|Požadováno|Použití|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Popisný název zobrazovaný v záhlaví **PickBranch** návrháře. Výchozí hodnota je větev.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je osvědčeným postupem je použití jednoho.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Hodnota TRUE|Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Trigger%2A> akce, který může vyvolat <xref:System.Activities.Statements.PickBranch.Action%2A>.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Každý <xref:System.Activities.Statements.PickBranch> obsahuje <xref:System.Activities.Statements.PickBranch.Action%2A> , která se spustí, pokud aktivuje.|  
  
## <a name="see-also"></a>Viz také  
 [Tok řízení](../workflow-designer/control-flow-activity-designers.md)   
 [Výběr aktivity](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Použití aktivity Pick](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)