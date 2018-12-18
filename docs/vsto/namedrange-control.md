---
title: NamedRange – ovládací prvek
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9c9bc4ff5b3515d5dcd4dab1eef81bf5c9abf979
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676493"
---
# <a name="namedrange-control"></a>NamedRange – ovládací prvek
  <xref:Microsoft.Office.Tools.Excel.NamedRange> Ovládací prvek je oblast, která má jedinečný název, zpřístupní události a může být vázaný na data. Další informace najdete v tématu [přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>Vytvoření ovládacího prvku  
 Můžete přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacích prvků na list aplikace Microsoft Office Excel v době návrhu nebo za běhu v projektech na úrovni dokumentu.  
  
 Můžete přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacích prvků na list za běhu v doplňku VSTO. Další informace najdete v tématu [postupy: Přidání namedrange – ovládací prvky do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Ve výchozím nastavení, nejsou trvalé dynamicky generovaný pojmenované oblasti do listu jako hostitele Určuje, kdy je uzavřen do listu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvky se skládat jen z rozsahů na konkrétní listy. <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvky nemůže mít relativní názvy, které se vztahují na všechny listy a nemůže skládat z rozsahů, které jsou rozmístěny dva nebo víc listů v sešitech (3D rozsahy).  
  
## <a name="bind-data-to-the-control"></a>Vytvoření vazby dat k ovládacímu prvku  
 Pojmenované oblasti zdají být dobrým kandidátem pro komplexní datové vazby, protože může mít mnoho buněk; rozsah je však pouze kolekce buněk, z nichž nelze mapovat snadno na konkrétní sloupce z datové sady. Proto <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvky se podporují jenom jednoduché datové vazby. <xref:Microsoft.Office.Tools.Excel.ListObject> Ovládací prvek lze použít pro rozšířené datové vazby. Další informace najdete v tématu [ListObject – ovládací prvek](../vsto/listobject-control.md).  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> Ovládací prvek může být vázán na zdroji dat pomocí <xref:System.Windows.Forms.Control.DataBindings%2A> vlastnosti. Výchozí vazby vlastnosti data <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek je <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.  
  
 Pokud prostřednictvím každý použitý mechanizmus, se aktualizuje data v datové sadě vázané <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek se změny projeví.  
  
## <a name="formatting"></a>Formátování  
 Který lze použít k formátování <xref:Microsoft.Office.Interop.Excel.Range> lze použít u <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku. To zahrnuje ohraničení, písma, číselných formátů a stylů.  
  
## <a name="rename-the-control"></a>Přejmenujte ovládací prvek  
 Po přidání <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do listu z **nástrojů**, Visual Studio automaticky vygeneruje název ovládacího prvku. Můžete změnit název v **vlastnosti** okna.  
  
## <a name="events"></a>Události  
 Tyto události jsou k dispozici pro <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku:  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>  
  
## <a name="see-also"></a>Viz také:  
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Ukázky vývoje pro Office a názorné postupy](../vsto/office-development-samples-and-walkthroughs.md)   
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Postupy: Změna velikosti ovládacích prvků NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Návod: Program ošetření událostí ovládacího prvku NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  