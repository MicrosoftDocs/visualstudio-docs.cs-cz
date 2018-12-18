---
title: 'Postupy: řazení dat na listech prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 179cf5fab5a1b2690cb4b46160f7a5c3342fe7bc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914211"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Postupy: řazení dat na listech prostřednictvím kódu programu
  Můžete řadit data obsažená v oblastech listů a seznamů v době běhu. Následující kód seřadí vícesloupcové oblast s názvem `Fruits` podle dat v prvním sloupci a poté podle data ve druhém sloupci.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="sort-data-in-a-document-level-customization"></a>Řazení dat v přizpůsobení na úrovni dokumentu  
  
### <a name="to-sort-data-in-a-namedrange-control"></a>Řazení dat v ovládacím prvku NamedRange  
  
1. Volání <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> metodu <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku. V následujícím příkladu vyžaduje <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `Fruits` v listu. Tento kód musí být umístěn ve třídě list, není v `ThisWorkbook` třídy.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
    [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]  
  
   Umístěte následující kód v *Sheet1.vb* nebo *Sheet1.cs* řazení dat v <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku. Kód předpokládá, že máte <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek s názvem `fruitList` na listu s názvem `Sheet1`.  
  
### <a name="to-sort-data-in-a-listobject-control"></a>Řazení dat v ovládacím prvku ListObject  
  
1.  Volání <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metodu <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> vlastnost <xref:Microsoft.Office.Tools.Excel.ListObject> hostování ovládacího prvku.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]  
  
## <a name="sort-data-in-a-vsto-add-in"></a>Řazení dat v doplňku VSTO  
  
### <a name="to-sort-data-in-a-native-range"></a>Řazení dat v nativní rozsahu  
  
1.  Volání <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metoda nativní aplikace Excel <xref:Microsoft.Office.Interop.Excel.Range> ovládacího prvku. V následujícím příkladu vyžaduje ovládací prvek nativní aplikace Excel s názvem `Fruits` v listu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]  
  
### <a name="to-sort-data-in-a-listobject-control"></a>Řazení dat v ovládacím prvku ListObject  
  
1.  Volání <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metodu <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> vlastnost nativní aplikace Excel <xref:Microsoft.Office.Interop.Excel.ListObject> ovládacího prvku. V následujícím příkladu se předpokládá, že máte nativní aplikace Excel <xref:Microsoft.Office.Interop.Excel.ListObject> ovládací prvek s názvem `fruitList` v aktivním listu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]  
  
## <a name="see-also"></a>Viz také:  
 [Práce s listy](../vsto/working-with-worksheets.md)   
 [Postupy: programové automatické vyplnění oblastí s přírůstkově se měnícími daty](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Postupy: odkazování na oblasti listů v kódu programu](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Postupy: používání stylů pro oblasti sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Namedrange – ovládací prvek](../vsto/namedrange-control.md)   
 [ListObject – ovládací prvek](../vsto/listobject-control.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  