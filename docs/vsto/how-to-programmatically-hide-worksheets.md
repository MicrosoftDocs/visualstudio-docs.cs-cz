---
title: 'Postupy: skrývání listů prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a60a0189af5608496e1f0f415a2d668e896af8e3
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676580"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Postupy: skrývání listů prostřednictvím kódu programu
  Můžete zobrazit nebo skrýt všechny listu v sešitu. Chcete-li skrýt listu, pomocí hostitelská položka worksheet nebo přistupovat ke listu pomocí kolekce listů sešitu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-the-worksheet-host-item"></a>Použití hostitelská položka worksheet  
 Pokud v době návrhu v přizpůsobení na úrovni dokumentu byla přidána do listu, použijte <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> vlastnost skrýt zadaného listu.  
  
### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Chcete-li skrýt na listu s použitím hostitelská položka worksheet  
  
1.  Nastavte <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> vlastnost `Sheet1` položka hostitele na <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> hodnota výčtu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Kolekce stylů Excelový sešit  
 Přístup k listů prostřednictvím aplikace Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Sheets> kolekce v následujících případech:  
  
-   Chcete skrýt sešitu v doplňku VSTO.  
  
-   List, který chcete skrýt byl vytvořen v době běhu v přizpůsobení na úrovni dokumentu.  
  
### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Chcete-li skrýt na listu s použitím kolekci seznamů sešitu aplikace Excel  
  
1.  Nastavte <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> vlastnost list <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> hodnota výčtu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]  
  
## <a name="see-also"></a>Viz také:  
 [Práce s listy](../vsto/working-with-worksheets.md)   
 [Postupy: odstraňování listů ze sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Postupy: přesouvání listů v sešitech prostřednictvím kódu programu](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Postupy: zamykání listů](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)  
  