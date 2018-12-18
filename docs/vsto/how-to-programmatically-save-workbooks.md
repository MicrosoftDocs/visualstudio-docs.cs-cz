---
title: 'Postupy: ukládání sešitů prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6fc715518f31031c65667a2480d7e14111105202
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676019"
---
# <a name="how-to-programmatically-save-workbooks"></a>Postupy: ukládání sešitů prostřednictvím kódu programu
  Existuje několik způsobů, jak uložit sešit. Sešit můžete uložit beze změny cesty. Pokud sešit nebyl uložen před, byste měli uložit sešit tak, že zadáte cestu. Bez explicitního cesty aplikace Microsoft Office Excel uloží soubor s názvem, který byl zadán při vytvoření rovnou uložil do aktuální složky. Můžete také uložit kopii tohoto sešitu beze změny otevřít sešit v paměti.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="save-a-workbook-without-changing-the-path"></a>Uložení sešitu beze změny cesty  
  
### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Uložte sešit přidružené k přizpůsobení úrovni dokumentu  
  
1.  Volání <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> metodu `ThisWorkbook` třídy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]  
  
### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Chcete-li uložit aktivním sešitu v doplňku VSTO  
  
1.  Volání <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> metoda má aktivní sešit uložit. Chcete-li použít následující příklad kódu, spusťte `ThisAddIn` třídy v projektu doplňku VSTO pro Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="save-a-workbook-with-a-new-path"></a>Uložení sešitu s novou cestou  
 Zadaný sešit můžete uložit do nového umístění nebo s novým názvem, volitelně může být zadáno formát souboru, hesla, režimu přístupu a další.  
  
> [!NOTE]  
>  Můžete chtít nastavit <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> vlastnost **False** před uložením sešitu s novou cestu, protože ukládá v některé formáty vyžaduje zásah. Nastavení této vlastnosti na **False** způsobí, že aplikace Excel a použijte všechny výchozí hodnoty.  
  
### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Uložte sešit přidružené k přizpůsobení úrovni dokumentu  
  
1.  Volání <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metodu `ThisWorkbook` třídy. Chcete-li použít následující příklad kódu, spusťte `ThisWorkbook` třídy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]  
  
### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Chcete-li uložit aktivním sešitu v doplňku VSTO  
  
1.  Volání <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> metoda má aktivní sešit uložit na novou cestu. Chcete-li použít následující příklad kódu, spusťte `ThisAddIn` třídy v projektu doplňku VSTO pro Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="save-a-copy-of-the-workbook"></a>Uložit kopii tohoto sešitu  
 Můžete uložit kopii tohoto sešitu do souboru beze změny otevřít sešit v paměti. To je užitečné, pokud chcete vytvořit záložní kopii beze změny umístění sešitu.  
  
### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Uložte sešit přidružené k přizpůsobení úrovni dokumentu  
  
1.  Volání <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> metodu `ThisWorkbook` třídy. Chcete-li použít následující příklad kódu, spusťte `ThisWorkbook` třídy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]  
  
### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Chcete-li uložit aktivním sešitu v doplňku VSTO  
  
1.  Volání <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> metody uložte kopii aktivního sešitu. Chcete-li použít následující příklad kódu, spusťte `ThisAddIn` třídy v projektu doplňku VSTO pro Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Interaktivní některou z metod, které uložit nebo zkopírovat sešit zrušení vyvolá chybu za běhu ve vašem kódu. Například, pokud procedura volá <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metoda, ale nemá, vyzve nelze zakázat z Excelu, a uživatel klikne **zrušit** po zobrazení výzvy, Excel, vyvolá chybu za běhu.  
  
## <a name="see-also"></a>Viz také:  
 [Práce se sešity](../vsto/working-with-workbooks.md)   
 [Hostitelská položka Workbook](../vsto/workbook-host-item.md)   
 [Postupy: zavírání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)  
  
  