---
title: 'Postupy: tisk listů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově tisknout libovolný list v sešitu Microsoft Excelu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 129493f726967776aa669eb92f6e912ed9c1b11b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827146"
---
# <a name="how-to-programmatically-print-worksheets"></a>Postupy: tisk listů prostřednictvím kódu programu

List můžete vytisknout v sešitu.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Tisk listu v přizpůsobení na úrovni dokumentu

### <a name="to-print-a-worksheet"></a>Tisk listu

1. Zavolejte `PrintOut` metodu `Sheet1` , vyžádejte si dvě kopie a zobrazte náhled dokumentu před tiskem.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet22":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet22":::

   <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>Metoda umožňuje zobrazit zadaný objekt v okně **Náhled tisku** . Následující kód předpokládá, že máte <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelskou položku s názvem `Sheet1` .

### <a name="to-preview-a-page-before-printing"></a>Náhled stránky před tiskem

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> metodu listu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet23":::

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Tisk listu v doplňku VSTO

### <a name="to-print-a-worksheet"></a>Tisk listu

1. Zavolejte <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> metodu aktivního listu, vyžádejte si dvě kopie a před tiskem dokument zobrazte.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet14":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet14":::

   <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>Metoda umožňuje zobrazit zadaný objekt v okně **Náhled tisku** .

### <a name="to-preview-a-page-before-printing"></a>Náhled stránky před tiskem

1. Zavolejte <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metodu aktivního listu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>Viz také

- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: Kontrola pravopisu v listech prostřednictvím kódu programu](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Položka hostitele listu](../vsto/worksheet-host-item.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
