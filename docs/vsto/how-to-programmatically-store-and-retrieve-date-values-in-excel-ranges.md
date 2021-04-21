---
title: Program Store & načíst hodnoty data v oblasti aplikace Excel programově
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově ukládat a načítat hodnoty data v oblastech Microsoft Excelu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6e3115e00147a5dff850f6e0c051ffc3b6733218
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826236"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Postupy: ukládání a načítání hodnot data v oblastech aplikace Excel prostřednictvím kódu programu
  Hodnoty můžete ukládat a načítat v <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacím prvku nebo v nativním objektu oblasti aplikace Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Pokud ukládáte hodnotu data, která spadá do rozsahu pomocí nástrojů pro vývoj pro Office v sadě Visual Studio nebo po ní 1/1/1900, je uložená ve formátu OLE Automation (OA). <xref:System.DateTime.FromOADate%2A>K načtení hodnoty dat OLE Automation (OA) musíte použít metodu. Pokud je datum dřívější než 1/1/1900, je uloženo jako řetězec.

> [!NOTE]
> Data v Excelu se liší od dat automatizace OLE za první dva měsíce od 1900. Existují také rozdíly v případě, že je zaškrtnuta možnost **1904 kalendářního systému** . Níže uvedené příklady kódu tyto rozdíly neřeší.

## <a name="use-a-namedrange-control"></a>Použití ovládacího prvku NamedRange

- Tento příklad je pro přizpůsobení na úrovni dokumentu. Následující kód musí být umístěn ve třídě listu, nikoli ve `ThisWorkbook` třídě.

### <a name="to-store-a-date-value-in-a-named-range"></a>Uložení hodnoty data v pojmenovaném rozsahu

1. Vytvoří <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek v buňce **a1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet50":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet50":::

2. Nastavte dnešní datum jako hodnotu pro `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet51":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet51":::

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Načtení hodnoty data z pojmenovaného rozsahu

1. Načte hodnotu data z `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet52":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet52":::

## <a name="use-native-excel-ranges"></a>Použít nativní oblasti aplikace Excel

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Uložení hodnoty data do nativního objektu excelového rozsahu

1. Vytvořte objekt <xref:Microsoft.Office.Interop.Excel.Range> , který představuje buňku **a1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet25":::

2. Nastavte dnešní datum jako hodnotu pro `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet26":::

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Načtení hodnoty data z nativního objektu excelového rozsahu

1. Načte hodnotu data z `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet27":::

## <a name="see-also"></a>Viz také
- [Práce s rozsahy](../vsto/working-with-ranges.md)
- [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Postupy: odkazování na oblasti listů v kódu prostřednictvím kódu programu](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
