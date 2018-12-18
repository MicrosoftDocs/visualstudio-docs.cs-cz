---
title: 'Postupy: Změna velikosti ovládacích prvků v buňkách listu'
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
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 91a7e66e085408b35f0ce1d8f7d4783e0c4715a8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676080"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Postupy: Změna velikosti ovládacích prvků v buňkách listu
  Při změně velikosti sloupce nebo řádky v listu, změnit velikost hostitelských ovládacích prvků v buňkách automaticky na výšku nebo šířku na buňku, která se změnila. Ovládací prvky Windows Forms se velikost automaticky ve výchozím nastavení.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Pokud chcete přidat ovládací prvky v době návrhu, musíte nastavit možnosti pro každý ovládací prvek umístění.  
  
 Pokud přidáte ovládací prvek Windows Forms prostřednictvím kódu programu a zadat argument rozsahu, ovládací prvek automaticky změní velikost při změně velikosti buněk v rámci rozsahu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="resize-controls-at-design-time"></a>Změna velikosti ovládacích prvků v době návrhu  
  
### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Chcete-li ovládací prvky, změna velikosti buněk v době návrhu  
  
1.  Z **nástrojů**, přetáhněte ovládací prvek Windows Forms do listu.  
  
2.  Klikněte pravým tlačítkem na ovládací prvek a potom klikněte na tlačítko **formát ovládacího prvku**.  
  
3.  V **formát ovládacího prvku** dialogové okno, klikněte na tlačítko **vlastnosti** kartu.  
  
4.  V části **umístění objektu**, vyberte **přesunutí a změna velikosti buněk** možnost a potom klikněte na tlačítko **OK**.  
  
     Když změníte velikost buňky, která obsahuje ovládací prvek, ovládací prvek přizpůsobí svou velikost buňky.  
  
## <a name="resize-controls-at-runtime"></a>Změna velikosti ovládacích prvků za běhu  
 Pokud přidáte ovládacího prvku Windows Forms v době běhu a předat <xref:Microsoft.Office.Interop.Excel.Range> jako umístění pro ovládací prvek, ovládací prvek automaticky změní velikost při změně velikosti na buňku listu, která obsahuje rozsah.  
  
### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Aby se změna velikosti buněk v době běhu ovládací prvky  
  
1.  Přidání ovládacího prvku na rozsah A1.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     Když změníte velikost buňky, která obsahuje ovládací prvek, ovládací prvek přizpůsobí svou velikost buňky.  
  
## <a name="reset-control-placement"></a>Obnovení umístění ovládacího prvku  
 Můžete resetovat, umístění a změnu velikosti ovládacího prvku tak, že nastavíte `Placement` vlastnost na jednu z následujících <xref:Microsoft.Office.Interop.Excel.XlPlacement> hodnoty:  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Chcete-li změnit chování ovládacího prvku tak, aby nepodporuje velikost ani přesunout s buňky  
  
1.  Třeba volat vlastnost umístění ovládacího prvku a nastavte hodnotu na <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>Viz také:  
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Postupy: skrytí ovládacích prvků na listech při tisku](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Omezení ovládacích prvků Windows Forms v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  