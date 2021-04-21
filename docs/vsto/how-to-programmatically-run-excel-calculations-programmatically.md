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
ms.openlocfilehash: 9fdc9cbc1966ac0fd862b795d66c7004f5089499
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823961"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Postupy: spouštění výpočtů v aplikaci Excel prostřednictvím kódu programu
  Podobný proces můžete použít ke spuštění výpočtů v <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacím prvku nebo v nativním objektu oblasti aplikace Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Spuštění výpočtů v ovládacím prvku NamedRange
 Následující příklad vytvoří <xref:Microsoft.Office.Tools.Excel.NamedRange> buňku a1 a pak vypočítá buňku. Tento kód musí být umístěn ve třídě listu, nikoli ve `ThisWorkbook` třídě.

### <a name="to-run-calculations-in-a-namedrange-control"></a>Spuštění výpočtů v ovládacím prvku NamedRange

1. Vytvořte pojmenovaný rozsah.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet75":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet75":::

2. Volejte <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> metodu zadaného rozsahu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet76":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet76":::

## <a name="run-calculations-in-a-native-excel-range"></a>Spuštění výpočtů v nativním rozsahu aplikace Excel

### <a name="to-run-calculations-in-a-native-excel-range"></a>Spuštění výpočtů v nativním rozsahu aplikace Excel

1. Vytvořte pojmenovaný rozsah.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet30":::

2. Volejte <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> metodu zadaného rozsahu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet31":::

## <a name="see-also"></a>Viz také
- [Práce s rozsahy](../vsto/working-with-ranges.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
