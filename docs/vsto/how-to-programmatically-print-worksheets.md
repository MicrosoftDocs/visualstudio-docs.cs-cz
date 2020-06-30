---
title: 'Postupy: tisk listů prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b0affdd34ad1cb302beacdc1abc9d02275878afd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537888"
---
# <a name="how-to-programmatically-print-worksheets"></a>Postupy: tisk listů prostřednictvím kódu programu

List můžete vytisknout v sešitu.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Tisk listu v přizpůsobení na úrovni dokumentu

### <a name="to-print-a-worksheet"></a>Tisk listu

1. Zavolejte `PrintOut` metodu `Sheet1` , vyžádejte si dvě kopie a zobrazte náhled dokumentu před tiskem.

    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]

   <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>Metoda umožňuje zobrazit zadaný objekt v okně **Náhled tisku** . Následující kód předpokládá, že máte <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelskou položku s názvem `Sheet1` .

### <a name="to-preview-a-page-before-printing"></a>Náhled stránky před tiskem

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> metodu listu.

     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Tisk listu v doplňku VSTO

### <a name="to-print-a-worksheet"></a>Tisk listu

1. Zavolejte <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> metodu aktivního listu, vyžádejte si dvě kopie a před tiskem dokument zobrazte.

    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]

   <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>Metoda umožňuje zobrazit zadaný objekt v okně **Náhled tisku** .

### <a name="to-preview-a-page-before-printing"></a>Náhled stránky před tiskem

1. Zavolejte <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metodu aktivního listu.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Viz také

- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: Kontrola pravopisu v listech prostřednictvím kódu programu](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Položka hostitele listu](../vsto/worksheet-host-item.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
