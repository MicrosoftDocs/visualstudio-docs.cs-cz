---
title: 'Postupy: spouštění výpočtů v aplikaci Excel prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově spouštět výpočty v sešitu Microsoft Excelu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 761f58027171ccaa667aa26569e41c3b4a8b75a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880473"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Postupy: spouštění výpočtů v aplikaci Excel prostřednictvím kódu programu
  Podobný proces můžete použít ke spuštění výpočtů v <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacím prvku nebo v nativním objektu oblasti aplikace Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Spuštění výpočtů v ovládacím prvku NamedRange
 Následující příklad vytvoří <xref:Microsoft.Office.Tools.Excel.NamedRange> buňku a1 a pak vypočítá buňku. Tento kód musí být umístěn ve třídě listu, nikoli ve `ThisWorkbook` třídě.

### <a name="to-run-calculations-in-a-namedrange-control"></a>Spuštění výpočtů v ovládacím prvku NamedRange

1. Vytvořte pojmenovaný rozsah.

     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]

2. Volejte <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> metodu zadaného rozsahu.

     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]

## <a name="run-calculations-in-a-native-excel-range"></a>Spuštění výpočtů v nativním rozsahu aplikace Excel

### <a name="to-run-calculations-in-a-native-excel-range"></a>Spuštění výpočtů v nativním rozsahu aplikace Excel

1. Vytvořte pojmenovaný rozsah.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]

2. Volejte <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> metodu zadaného rozsahu.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]

## <a name="see-also"></a>Viz také
- [Práce s rozsahy](../vsto/working-with-ranges.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
