---
title: 'Postupy: Změna velikosti ovládacích prvků NamedRange'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6d785aba9d08f71aa8530bc2edd015f497caafef
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675678"
---
# <a name="how-to-resize-namedrange-controls"></a>Postupy: Změna velikosti ovládacích prvků NamedRange
  Můžete nastavit velikost <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek, když ho přidáte do dokumentu aplikace Microsoft Office Excel; však můžete chtít změnit jeho velikost později.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Pojmenované oblasti můžete změnit velikost v době návrhu nebo za běhu v projektech na úrovni dokumentu. Můžete taky změnit velikost pojmenované oblasti za běhu v úrovni aplikace doplňků VSTO.  
  
 Toto téma popisuje následující úkoly:  
  
-   [Změna velikosti ovládacích prvků NamedRange v době návrhu](#designtime)  
  
-   [Změna velikosti ovládacích prvků NamedRange za běhu v projektu úrovni dokumentu](#runtimedoclevel)  
  
-   [Změna velikosti ovládacích prvků NamedRange za běhu v projektu doplňku VSTO](#runtimeaddin)  
  
##  <a name="designtime"></a> Změna velikosti ovládacích prvků NamedRange v době návrhu  
 Pojmenované oblasti můžete změnit velikost, v jeho velikost, nově definují obor **definovat název** dialogové okno.  
  
### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Změna velikosti pojmenované oblasti s použitím definovat název dialogových oken  
  
1.  Klikněte pravým tlačítkem myši <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku.  
  
2.  Klikněte na tlačítko **oblasti spravovat** v místní nabídce.  
  
     **Definovat název** zobrazí se dialogové okno.  
  
3.  Vyberte oblast s názvem, který chcete změnit velikost.  
  
4.  Zrušte **odkazuje na** pole.  
  
5.  Vyberte buňky, které chcete použít pro definování velikosti pojmenovaném rozsahu.  
  
6.  Klikněte na tlačítko **OK**.  
  
##  <a name="runtimedoclevel"></a> Změna velikosti ovládacích prvků NamedRange za běhu v projektu úrovni dokumentu  
 Můžete změnit velikost pojmenované oblasti programově pomocí <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> vlastnost.  
  
> [!NOTE]  
>  V **vlastnosti** okno, <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> vlastnost je označena jako jen pro čtení.  
  
### <a name="to-resize-a-named-range-programmatically"></a>Změna velikosti pojmenované oblasti prostřednictvím kódu programu  
  
1.  Vytvoření <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku v buňce **A1** z `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]  
  
2.  Změna velikosti pojmenované oblasti zahrnout buňky **B1**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> Změna velikosti ovládacích prvků NamedRange za běhu v projektu doplňku VSTO  
 Můžete změnit velikost <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek na jakékoli otevřete list za běhu. Další informace o tom, jak přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> řídit do listu pomocí doplňku VSTO, přečtěte si téma [postupy: ovládací prvky přidat NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
### <a name="to-resize-a-named-range-programmatically"></a>Změna velikosti pojmenované oblasti prostřednictvím kódu programu  
  
1.  Vytvoření <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku v buňce **A1** z `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]  
  
2.  Změna velikosti pojmenované oblasti zahrnout buňky **B1**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]  
  
## <a name="see-also"></a>Viz také:  
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Namedrange – ovládací prvek](../vsto/namedrange-control.md)   
 [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Postupy: Změna velikosti ovládacích prvků záložek](../vsto/how-to-resize-bookmark-controls.md)   
 [Postupy: Změna velikosti ovládacích prvků ListObject](../vsto/how-to-resize-listobject-controls.md)  
  
  