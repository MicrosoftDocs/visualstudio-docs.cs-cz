---
title: 'Postupy: spouštění výpočtů v aplikaci Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0dabde287d71736ab49f35acf968300bccee0d12
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675661"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Postupy: spouštění výpočtů v aplikaci Excel  
  Podobný proces používáte ke spouštění výpočtů <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek nebo rozsah objekt nativní aplikace Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="run-calculations-in-a-namedrange-control"></a>Spouštění výpočtů v ovládacím prvku NamedRange  
 Následující příklad vytvoří <xref:Microsoft.Office.Tools.Excel.NamedRange> do buňky A1 a vypočítá jeho buňku. Tento kód musí být umístěn ve třídě list, není v `ThisWorkbook` třídy.  
  
### <a name="to-run-calculations-in-a-namedrange-control"></a>Spouštění výpočtů v ovládacím prvkem namedrange  
  
1.  Vytvoření pojmenovaného rozsahu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]  
  
2.  Volání <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> metoda určeného rozsahu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]  
  
## <a name="run-calculations-in-a-native-excel-range"></a>Spouštění výpočtů v nativní Excelového rozsahu  
  
### <a name="to-run-calculations-in-a-native-excel-range"></a>Spouštění výpočtů v nativní Excelového rozsahu  
  
1.  Vytvoření pojmenovaného rozsahu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]  
  
2.  Volání <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> metoda určeného rozsahu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]  
  
## <a name="see-also"></a>Viz také:  
 [Práce s oblastmi](../vsto/working-with-ranges.md)   
 [Namedrange – ovládací prvek](../vsto/namedrange-control.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  