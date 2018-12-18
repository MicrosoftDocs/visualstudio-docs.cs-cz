---
title: 'Postupy: výběr listů prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09e477d802b9d92ca4f9e1cd3a532145ad0e68a0
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676629"
---
# <a name="how-to-programmatically-select-worksheets"></a>Postupy: výběr listů prostřednictvím kódu programu
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> Metoda vybere zadaný objekt, který přesune výběr uživatele na nový objekt. Použití <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> metody, pokud chcete vyvést fokus na objekt beze změny výběru uživatele.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Pokud chcete vybrat existujícího listu v doplňku VSTO nebo pokud sešit byl vytvořen za běhu v přizpůsobení na úrovni dokumentu, je zapotřebí k němu přistoupit pomocí aplikace Excel <xref:Microsoft.Office.Interop.Excel.Sheets> kolekce sešitu aplikace Excel; v opačném případě můžete přistupovat <xref:Microsoft.Office.Tools.Excel.Worksheet>hostitelský objekt přímo.  
  
## <a name="use-the-worksheet-host-item"></a>Použití hostitelská položka worksheet  
 V přizpůsobení na úrovni dokumentu, přidejte následující kód, který *Sheet1.vb* nebo *Sheet1.cs*.  
  
### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Vyberte první sešit v pomocí hostitelská položka sešitu  
  
1.  Volání <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> metoda `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Kolekce stylů Excelový sešit  
 Přístup pomocí aplikace Excel listu <xref:Microsoft.Office.Interop.Excel.Sheets> kolekce.  
  
### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Vyberte první listu v sešitu pomocí kolekce listech sešitu aplikace Excel  
  
1.  Volání <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> metodu <xref:Microsoft.Office.Interop.Excel.Sheets> kolekci vyberte první sešit aktivním sešitu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]  
  
## <a name="see-also"></a>Viz také:  
 [Práce s listy](../vsto/working-with-worksheets.md)   
 [Postupy: tisk listů prostřednictvím kódu programu](../vsto/how-to-programmatically-print-worksheets.md)   
 [Postupy: odstraňování listů ze sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Postupy: skrývání listů prostřednictvím kódu programu](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Postupy: zamykání listů](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Hostitelská položka Worksheet](../vsto/worksheet-host-item.md)   
 [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)  
  
  