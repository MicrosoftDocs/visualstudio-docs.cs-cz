---
title: 'Postupy: Přidání ovládacích prvků graf do listů'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 713657c7df5bfd3dd3f864c15ffc86dd1d531eac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919920"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Postupy: Přidání ovládacích prvků graf do listů
  Můžete přidat <xref:Microsoft.Office.Tools.Excel.Chart> ovládacích prvků na list aplikace Microsoft Office Excel v době návrhu a za běhu v přizpůsobeních na úrovni dokumentu. Můžete také přidat <xref:Microsoft.Office.Tools.Excel.Chart> ovládacích prvků za běhu v doplňcích VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Toto téma popisuje následující úkoly:  
  
- [Přidání ovládacích prvků graf v době návrhu](#designtime)  
  
- [Přidání ovládacích prvků graf za běhu v projektu úrovni dokumentu](#runtimedoclevel)  
  
- [Přidání ovládacích prvků graf za běhu v projektu doplňku VSTO](#runtimeaddin)  
  
  Další informace o <xref:Microsoft.Office.Tools.Excel.Chart> ovládacích prvků, naleznete v tématu [ovládacího prvku grafu](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Přidání ovládacích prvků graf v době návrhu  
 Můžete přidat <xref:Microsoft.Office.Tools.Excel.Chart> ovládacího prvku do listu stejným způsobem, přidejte grafu z v rámci aplikace.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart> Ovládací prvek není k dispozici **nástrojů** nebo **zdroje dat** okna.  
  
### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Přidání hostitelského ovládacího prvku grafu do listu aplikace Excel  
  
1.  Na **vložit** kartě **grafy** klikněte na možnost **sloupec**, klepněte na kategorii grafy a potom klikněte na typ grafu chcete.  
  
2.  V **vložit graf** dialogové okno, klikněte na tlačítko **OK**.  
  
3.  Na **návrhu** kartě **Data** klikněte na možnost **vybrat Data**.  
  
4.  V **vybrat zdroj dat** dialogové okno, kliknutím na webu **grafu** **oblast dat** a zrušte všechny výchozí výběr.  
  
5.  V **Data grafu** listu, vyberte oblast buněk, který obsahuje data grafu (buňky **A5** prostřednictvím **D8**).  
  
6.  V **vybrat zdroj dat** dialogové okno, klikněte na tlačítko **OK**.  
  
##  <a name="runtimedoclevel"></a> Přidání ovládacích prvků graf za běhu v projektu úrovni dokumentu  
 Můžete přidat <xref:Microsoft.Office.Tools.Excel.Chart> ovládací prvek dynamicky za běhu. Dynamicky generovaný grafy nejsou zachované v dokumentu jako hostitele určuje při zavření dokumentu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Přidání ovládacího prvku grafu na listu prostřednictvím kódu programu  
  
1.  V <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obslužná rutina události `Sheet1`, vložte následující kód pro přidání <xref:Microsoft.Office.Tools.Excel.Chart> ovládacího prvku.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Přidání ovládacích prvků graf za běhu v projektu doplňku VSTO  
 Můžete přidat <xref:Microsoft.Office.Tools.Excel.Chart> řízení prostřednictvím kódu programu k žádné otevřené listu v projektu doplňku VSTO. Další informace najdete v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Ovládací prvky dynamicky generovaný grafu nejsou zachované v listu jako hostitele Určuje, kdy je uzavřen do listu. Další informace najdete v tématu [dokumenty přidat ovládací prvky pro Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Přidání ovládacího prvku grafu na listu prostřednictvím kódu programu  
  
1.  Následující kód vygeneruje hostitelská položka worksheet, která je založená na open listu a potom přidá <xref:Microsoft.Office.Tools.Excel.Chart> ovládacího prvku.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 V tomto příkladu má následující požadavky:  
  
-   Data mají vykreslovat do grafů, uložená v rozsahu od A5 do D8 v listu.  
  
## <a name="see-also"></a>Viz také:  
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Graf – ovládací prvek](../vsto/chart-control.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  